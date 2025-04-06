# Static analyzer annotations for GC correctness in C code

## Running the analysis

분석을 수행하는 분석기 플러그인은 줄리아와 함께 제공됩니다. 소스 코드는 `src/clangsa`에 있습니다. 이를 실행하려면 clang 의존성을 빌드해야 합니다. 적절한 버전의 clang을 빌드하기 위해 Make.user에서 `BUILD_LLVM_CLANG` 변수를 설정하세요. 또한 `USE_BINARYBUILDER_LLVM` 옵션을 사용하여 미리 빌드된 바이너리를 사용할 수도 있습니다.

대안으로 (또는 이것들이 충분하지 않은 경우), 시도해 보세요.

```sh
make -C src install-analysis-deps
```

줄리아의 최상위 디렉토리에서.

그 후, 소스 트리에 대한 분석을 실행하는 것은 `make -C src analyzegc`를 실행하는 것만큼 간단합니다.

## General Overview

줄리아의 GC는 정밀하기 때문에 GC가 발생할 수 있는 모든 시점에서 참조될 수 있는 값에 대한 올바른 루팅 정보를 유지해야 합니다. 이러한 장소를 `safepoints`라고 하며, 함수의 로컬 컨텍스트에서는 이 지정을 재귀적으로 safepoint에 도달할 수 있는 모든 함수 호출로 확장합니다.

생성된 코드에서는 GC 루트 배치 패스에 의해 자동으로 처리됩니다(LLVM 코드 생성 개발 문서의 GC 루팅 장 참조). 그러나 C 코드에서는 런타임에 모든 GC 루트를 수동으로 알려줘야 합니다. 이는 다음 매크로를 사용하여 수행됩니다:

```
// The value assigned to any slot passed as an argument to these
// is rooted for the duration of this GC frame.
JL_GC_PUSH{1,...,6}(args...)
// The values assigned into the size `n` array `rts` are rooted
// for the duration of this GC frame.
JL_GC_PUSHARGS(rts, n)
// Pop a GC frame
JL_GC_POP
```

이 매크로가 필요한 곳에서 사용되지 않거나 잘못 사용되면, 결과는 조용한 메모리 손상입니다. 따라서 모든 적용 가능한 코드에서 올바르게 배치되는 것이 매우 중요합니다.

이와 같이, 우리는 이러한 매크로가 올바르게 사용되도록 돕기 위해 정적 분석(특히 clang 정적 분석기)을 사용합니다. 이 문서의 나머지 부분에서는 이 정적 분석에 대한 개요를 제공하고, 이를 작동시키기 위해 julia 코드베이스에서 필요한 지원을 설명합니다.

## GC Invariants

두 가지 간단한 불변성의 정확성:

  * 모든 `GC_PUSH` 호출은 적절한 `GC_POP`으로 이어져야 합니다 (실제로 우리는 이를 함수 수준에서 강제합니다).
  * 값이 이전에 어떤 세이프포인트에서도 루팅되지 않았다면, 이후에는 더 이상 참조되지 않을 수 있습니다.

물론 세부 사항에 악마가 있습니다. 특히 위의 두 번째 조건을 충족하기 위해 우리는 다음을 알아야 합니다:

  * 어떤 호출이 안전 지점이고 어떤 호출이 아닌지
  * 어떤 주어진 안전 지점에서 어떤 값이 루트되고 어떤 값이 루트되지 않는지
  * 값이 참조되는 시점은 언제인가요?

특히 두 번째 포인트에 대해, 런타임에 어떤 메모리 위치가 루팅으로 간주될 것인지 알아야 합니다(즉, 이러한 위치에 할당된 값이 루팅됩니다). 여기에는 `GC_PUSH` 매크로 중 하나에 전달하여 명시적으로 지정된 위치, 전역적으로 루팅된 위치 및 값, 그리고 이러한 위치 중 하나에서 재귀적으로 도달 가능한 모든 위치가 포함됩니다.

## Static Analysis Algorithm

아이디어 자체는 매우 간단하지만, 구현은 상당히 복잡합니다(주로 많은 수의 특수 케이스와 C 및 C++의 복잡성 때문입니다). 본질적으로, 우리는 루트가 있는 모든 위치, 루트가 가능한 모든 값, 그리고 어떤 표현식(할당, 할당 등)이 루트가 가능한 값의 루트 상태에 영향을 미치는지를 추적합니다. 그런 다음, 안전 지점에서 "상징적 GC"를 수행하고 해당 위치에서 루트가 아닌 모든 값을 독으로 처리합니다. 이러한 값이 나중에 참조되면 오류를 발생시킵니다.

클랭 정적 분석기는 상태의 그래프를 구성하고 이 그래프를 탐색하여 오류의 원인을 찾는 방식으로 작동합니다. 이 그래프의 여러 노드는 분석기 자체에 의해 생성되지만(예: 제어 흐름), 위의 정의는 우리의 상태로 이 그래프를 보강합니다.

정적 분석기는 절차 간(interprocedural)이며 함수 경계를 넘어 제어 흐름을 분석할 수 있습니다. 그러나 정적 분석기는 완전히 재귀적이지 않으며 탐색할 호출에 대한 휴리스틱 결정을 내립니다(추가로 일부 호출은 번역 단위 간(cross-translation unit)이며 분석기에 보이지 않습니다). 우리의 경우, 정확성에 대한 정의는 전체 정보를 요구합니다. 따라서 우리는 분석에 필요한 모든 정보를 사용하여 모든 함수 호출의 프로토타입에 주석을 달아야 하며, 그 정보가 절차 간 정적 분석을 통해 제공될 수 있는 경우라도 마찬가지입니다.

다행히도 우리는 여전히 이 절차 간 분석을 사용하여 특정 함수에 부여한 주석이 해당 함수의 구현에 비추어 올바른지 확인할 수 있습니다.

## The analyzer annotations

이 주석은 src/support/analyzer_annotations.h에서 발견됩니다. 분석기가 사용될 때만 활성화되며, 프로토타입 주석의 경우 아무것도 아닌 것으로 확장되거나 함수와 같은 주석의 경우 no-op으로 확장됩니다.

### `JL_NOTSAFEPOINT`

이것은 아마도 가장 일반적인 주석이며, GC 안전 지점에 도달할 가능성이 없는 것으로 알려진 모든 함수에 배치되어야 합니다. 일반적으로 이러한 함수는 산술 연산, 메모리 접근 및 `JL_NOTSAFEPOINT`로 주석이 달린 함수 또는 그렇지 않더라도 안전 지점이 아닌 것으로 알려진 함수(예: 분석기에서 하드코딩된 C 표준 라이브러리의 함수)를 호출하는 것이 안전합니다.

이 속성으로 주석이 달린 모든 함수 호출 간에 값을 루트하지 않고 유지하는 것은 유효합니다:

사용 예:

```c
void jl_get_one() JL_NOTSAFEPOINT {
  return 1;
}

jl_value_t *example() {
  jl_value_t *val = jl_alloc_whatever();
  // This is valid, even though `val` is unrooted, because
  // jl_get_one is not a safepoint
  jl_get_one();
  return val;
}
```

### `JL_MAYBE_UNROOTED`/`JL_ROOTS_TEMPORARILY`

`JL_MAYBE_UNROOTED`가 함수의 인수로 주석 처리되면, 해당 인수가 루트가 아니더라도 전달될 수 있음을 나타냅니다. 일반적인 경우에, 줄리아 ABI는 호출자가 값을 호출 대상에 전달하기 전에 루트화하도록 보장합니다. 그러나 일부 함수는 이 ABI를 따르지 않으며 루트화되지 않은 값을 전달할 수 있도록 허용합니다. 그러나 이는 해당 인수가 자동으로 보존된다는 것을 의미하지는 않습니다. `ROOTS_TEMPORARILY` 주석은 값이 전달될 때 루트화되지 않을 수 있을 뿐만 아니라, 호출 대상에 의해 내부 안전 지점에서 보존될 것이라는 더 강력한 보장을 제공합니다.

`JL_NOTSAFEPOINT`는 본질적으로 `JL_MAYBE_UNROOTED`/`JL_ROOTS_TEMPORARILY`를 의미합니다. 함수에 safepoint가 포함되어 있지 않다면 인수의 루트 여부는 중요하지 않기 때문입니다.

하나 추가로 주목할 점은 이러한 주석이 호출자와 피호출자 측 모두에 적용된다는 것입니다. 호출자 측에서는 일반적으로 julia ABI 함수에 필요로 하는 뿌리 제한을 해제합니다. 피호출자 측에서는 이러한 인수가 암묵적으로 뿌리 있는 것으로 간주되는 것을 방지하는 반대 효과를 가집니다.

이 주석 중 하나가 함수 전체에 적용되면, 이는 함수의 모든 인수에 적용됩니다. 일반적으로 이는 varargs 함수에만 필요합니다.

사용 예:

```c
JL_DLLEXPORT void JL_NORETURN jl_throw(jl_value_t *e JL_MAYBE_UNROOTED);
jl_value_t *jl_alloc_error();

void example() {
  // The return value of the allocation is unrooted. This would normally
  // be an error, but is allowed because of the above annotation.
  jl_throw(jl_alloc_error());
}
```

### `JL_PROPAGATES_ROOT`

이 주석은 다른 객체 내에 저장된 하나의 루트 가능한 객체를 반환하는 접근자 함수에서 일반적으로 발견됩니다. 함수 인수에 주석이 달리면, 분석기에게 해당 인수의 루트가 함수가 반환하는 값에도 적용된다는 것을 알려줍니다.

사용 예:

```c
jl_value_t *jl_svecref(jl_svec_t *t JL_PROPAGATES_ROOT, size_t i) JL_NOTSAFEPOINT;

size_t example(jl_svec_t *svec) {
  jl_value_t *val = jl_svecref(svec, 1)
  // This is valid, because, as annotated by the PROPAGATES_ROOT annotation,
  // jl_svecref propagates the rooted-ness from `svec` to `val`
  jl_gc_safepoint();
  return jl_unbox_long(val);
}
```

### `JL_ROOTING_ARGUMENT`/`JL_ROOTED_ARGUMENT`

이것은 본질적으로 `JL_PROPAGATES_ROOT`의 할당 대응물입니다. 이미 루트가 있는 다른 값의 필드에 값을 할당할 때, 할당된 값은 할당된 값의 루트를 상속받습니다.

사용 예:

```c
void jl_svecset(void *t JL_ROOTING_ARGUMENT, size_t i, void *x JL_ROOTED_ARGUMENT) JL_NOTSAFEPOINT


size_t example(jl_svec_t *svec) {
  jl_value_t *val = jl_box_long(10000);
  jl_svecset(svec, val);
  // This is valid, because the annotations imply that the
  // jl_svecset propagates the rooted-ness from `svec` to `val`
  jl_gc_safepoint();
  return jl_unbox_long(val);
}
```

### `JL_GC_DISABLED`

이 주석은 이 함수가 GC 런타임이 비활성화된 상태에서만 호출된다는 것을 의미합니다. 이러한 종류의 함수는 주로 시작 시와 GC 코드 자체에서 자주 발견됩니다. 이 주석은 런타임 활성화/비활성화 호출에 대해 확인되므로, clang은 당신이 거짓말을 하는지 알 수 있습니다. GC가 실제로 비활성화되지 않은 경우 주어진 함수의 처리를 비활성화하는 좋은 방법이 아닙니다(필요하다면 `ifdef __clang_analyzer__`를 사용하세요).

사용 예:

```c
void jl_do_magic() JL_GC_DISABLED {
  // Wildly allocate here with no regard for roots
}

void example() {
  int en = jl_gc_enable(0);
  jl_do_magic();
  jl_gc_enable(en);
}
```

### `JL_REQUIRE_ROOTED_SLOT`

이 주석은 호출자가 루트된 슬롯을 전달해야 함을 요구합니다(즉, 이 슬롯에 할당된 값은 루트됩니다).

사용 예:

```c
void jl_do_processing(jl_value_t **slot JL_REQUIRE_ROOTED_SLOT) {
  *slot = jl_box_long(1);
  // Ok, only, because the slot was annotated as rooting
  jl_gc_safepoint();
}

void example() {
  jl_value_t *slot = NULL;
  JL_GC_PUSH1(&slot);
  jl_do_processing(&slot);
  JL_GC_POP();
}
```

### `JL_GLOBALLY_ROOTED`

이 주석은 주어진 값이 항상 전역적으로 루트된다는 것을 의미합니다. 이는 전역 변수 선언에 적용될 수 있으며, 이 경우 해당 변수의 값(또는 배열 선언의 경우 값들)에 적용됩니다. 또는 함수에 적용될 수 있으며, 이 경우 그러한 함수의 반환 값에 적용됩니다(예: 항상 일부 개인적이고 전역적으로 루트된 값을 반환하는 함수의 경우).

사용 예:

```
extern JL_DLLEXPORT jl_datatype_t *jl_any_type JL_GLOBALLY_ROOTED;
jl_ast_context_t *jl_ast_ctx(fl_context_t *fl) JL_GLOBALLY_ROOTED;
```

### `JL_ALWAYS_LEAFTYPE`

이 주석은 본질적으로 `JL_GLOBALLY_ROOTED`와 동등하지만, leaftype이기 때문에 전역적으로 루트가 되어야 하는 경우에만 사용해야 합니다. leaftype의 루팅은 다소 복잡합니다. 일반적으로 해당 `TypeName`의 `cache` 필드를 통해 루트가 되며, 이 필드는 포함된 모듈에 의해 루트가 됩니다(즉, 포함된 모듈이 괜찮은 한 루트가 됩니다). 일반적으로 leaftype이 사용되는 곳에서 루트가 되어 있다고 가정할 수 있지만, 향후 이 속성을 세분화할 수 있으므로 별도의 주석이 전역적으로 루트가 되는 이유를 분리하는 데 도움이 됩니다.

분석기는 또한 leaftype-ness에 대한 검사를 자동으로 감지하며 이러한 경로에서 누락된 GC 루트에 대해 불평하지 않습니다.

```
JL_DLLEXPORT jl_value_t *jl_apply_array_type(jl_value_t *type, size_t dim) JL_ALWAYS_LEAFTYPE;
```

### `JL_GC_PROMISE_ROOTED`

이것은 함수와 유사한 주석입니다. 이 주석에 전달된 모든 값은 현재 함수의 범위에 대해 루트로 간주됩니다. 이는 분석기의 불완전성이나 복잡한 상황을 위한 탈출구로 설계되었습니다. 그러나 분석기를 개선하는 것을 선호하여 드물게 사용해야 합니다.

```
void example() {
  jl_value_t *val = jl_alloc_something();
  if (some_condition) {
    // We happen to know for complicated external reasons
    // that val is rooted under these conditions
    JL_GC_PROMISE_ROOTED(val);
  }
}
```

## Completeness of analysis

분석기는 로컬 정보만을 살펴봅니다. 특히, 위의 `PROPAGATES_ROOT` 사례에서처럼, 그러한 메모리는 분석기가 볼 수 있는 방식으로만 수정된다고 가정하며, 호출된 함수에서 수정되거나 동시에 실행되는 스레드에서는 수정되지 않는다고 가정합니다. 따라서 몇 가지 문제 있는 경우를 놓칠 수 있지만, 실제로 그러한 동시 수정은 상당히 드뭅니다. 더 많은 이러한 경우를 처리하도록 분석기를 개선하는 것은 향후 작업에 흥미로운 주제가 될 수 있습니다.
