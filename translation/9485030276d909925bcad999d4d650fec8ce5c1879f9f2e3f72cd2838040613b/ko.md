# Embedding Julia

우리가 [Calling C and Fortran Code](@ref)에서 본 바와 같이, Julia는 C로 작성된 함수를 호출하는 간단하고 효율적인 방법을 제공합니다. 그러나 반대의 경우, 즉 C 코드에서 Julia 함수를 호출해야 하는 상황도 있습니다. 이는 Julia 코드를 더 큰 C/C++ 프로젝트에 통합하는 데 사용될 수 있으며, 모든 것을 C/C++로 다시 작성할 필요가 없습니다. Julia는 이를 가능하게 하는 C API를 제공합니다. 거의 모든 프로그래밍 언어는 C 함수를 호출하는 방법이 있으므로, Julia C API는 추가적인 언어 브리지를 구축하는 데에도 사용될 수 있습니다(예: Python, Rust 또는 C#에서 Julia 호출). Rust와 C++는 C 임베딩 API를 직접 사용할 수 있지만, 두 언어 모두 이를 돕는 패키지가 있으며, C++의 경우 [Jluna](https://github.com/Clemapfel/jluna)가 유용합니다.

## High-Level Embedding

**참고**: 이 섹션에서는 유닉스 계열 운영 체제에서 C에 Julia 코드를 임베드하는 방법을 다룹니다. Windows에서 이를 수행하려면, 그 다음 섹션인 [High-Level Embedding on Windows with Visual Studio](@ref)를 참조하십시오.

우리는 Julia를 초기화하고 일부 Julia 코드를 호출하는 간단한 C 프로그램으로 시작합니다:

```c
#include <julia.h>
JULIA_DEFINE_FAST_TLS // only define this once, in an executable (not in a shared library) if you want fast code.

int main(int argc, char *argv[])
{
    /* required: setup the Julia context */
    jl_init();

    /* run Julia commands */
    jl_eval_string("print(sqrt(2.0))");

    /* strongly recommended: notify Julia that the
         program is about to terminate. this allows
         Julia time to cleanup pending write requests
         and run all finalizers
    */
    jl_atexit_hook(0);
    return 0;
}
```

이 프로그램을 빌드하려면 Julia 헤더의 경로를 포함 경로에 추가하고 `libjulia`에 링크해야 합니다. 예를 들어, Julia가 `$JULIA_DIR`에 설치된 경우, 위의 테스트 프로그램 `test.c`를 `gcc`를 사용하여 컴파일할 수 있습니다:

```
gcc -o test -fPIC -I$JULIA_DIR/include/julia -L$JULIA_DIR/lib -Wl,-rpath,$JULIA_DIR/lib test.c -ljulia
```

대안으로, Julia 소스 트리의 `test/embedding/` 폴더에 있는 `embedding.c` 프로그램을 살펴보세요. 파일 `cli/loader_exe.c` 프로그램은 `libjulia`에 링크할 때 `jl_options` 옵션을 설정하는 방법에 대한 또 다른 간단한 예입니다.

Julia C 함수를 호출하기 전에 반드시 수행해야 할 첫 번째 작업은 Julia를 초기화하는 것입니다. 이는 `jl_init`을 호출하여 자동으로 Julia의 설치 위치를 결정하려고 시도합니다. 사용자 지정 위치를 지정하거나 로드할 시스템 이미지를 지정해야 하는 경우 대신 `jl_init_with_image`를 사용하십시오.

테스트 프로그램의 두 번째 문장은 `jl_eval_string` 호출을 사용하여 Julia 문장을 평가합니다.

프로그램이 종료되기 전에 `jl_atexit_hook`를 호출하는 것이 강력히 권장됩니다. 위의 예제 프로그램은 `main`에서 반환하기 직전에 이를 호출합니다.

!!! note
    현재 `libjulia` 공유 라이브러리와 동적으로 연결하려면 `RTLD_GLOBAL` 옵션을 전달해야 합니다. Python에서는 다음과 같이 보입니다:

    ```
    >>> julia=CDLL('./libjulia.dylib',RTLD_GLOBAL)
    >>> julia.jl_init.argtypes = []
    >>> julia.jl_init()
    250593296
    ```


!!! note
    만약 줄리아 프로그램이 메인 실행 파일의 심볼에 접근해야 한다면, 아래에 설명된 `julia-config.jl`에 의해 생성된 것 외에 리눅스에서 컴파일 시 `-Wl,--export-dynamic` 링커 플래그를 추가해야 할 수 있습니다. 공유 라이브러리를 컴파일할 때는 이 작업이 필요하지 않습니다.


### Using julia-config to automatically determine build parameters

스크립트 `julia-config.jl`은 임베디드 Julia를 사용하는 프로그램에 필요한 빌드 매개변수를 결정하는 데 도움을 주기 위해 생성되었습니다. 이 스크립트는 호출된 특정 Julia 배포판의 빌드 매개변수와 시스템 구성을 사용하여 해당 배포판과 상호 작용하는 임베딩 프로그램에 필요한 컴파일러 플래그를 내보냅니다. 이 스크립트는 Julia 공유 데이터 디렉토리에 위치해 있습니다.

#### Example

```c
#include <julia.h>

int main(int argc, char *argv[])
{
    jl_init();
    (void)jl_eval_string("println(sqrt(2.0))");
    jl_atexit_hook(0);
    return 0;
}
```

#### On the command line

이 스크립트의 간단한 사용법은 명령줄에서입니다. `julia-config.jl`이 `/usr/local/julia/share/julia`에 위치한다고 가정할 때, 명령줄에서 직접 호출할 수 있으며 세 가지 플래그의 조합을 사용할 수 있습니다:

```
/usr/local/julia/share/julia/julia-config.jl
Usage: julia-config [--cflags|--ldflags|--ldlibs]
```

위의 예제 소스가 `embed_example.c` 파일에 저장되어 있다면, 다음 명령어를 사용하여 Linux 및 Windows (MSYS2 환경)에서 실행 가능한 프로그램으로 컴파일할 수 있습니다. macOS에서는 `gcc` 대신 `clang`을 사용하세요.:

```
/usr/local/julia/share/julia/julia-config.jl --cflags --ldflags --ldlibs | xargs gcc embed_example.c
```

#### Use in Makefiles

일반적으로 임베딩 프로젝트는 위의 예보다 더 복잡할 것이며, 따라서 다음은 일반적인 makefile 지원을 허용합니다. **shell** 매크로 확장을 사용하기 때문에 GNU make를 가정합니다. 또한, `julia-config.jl`이 일반적으로 `/usr/local` 디렉토리에 있지만, 그렇지 않은 경우 Julia 자체를 사용하여 `julia-config.jl`을 찾을 수 있으며, makefile은 이를 활용할 수 있습니다. 위의 예는 makefile을 사용하도록 확장됩니다:

```
JL_SHARE = $(shell julia -e 'print(joinpath(Sys.BINDIR, Base.DATAROOTDIR, "julia"))')
CFLAGS   += $(shell $(JL_SHARE)/julia-config.jl --cflags)
CXXFLAGS += $(shell $(JL_SHARE)/julia-config.jl --cflags)
LDFLAGS  += $(shell $(JL_SHARE)/julia-config.jl --ldflags)
LDLIBS   += $(shell $(JL_SHARE)/julia-config.jl --ldlibs)

all: embed_example
```

이제 빌드 명령은 단순히 `make`입니다.

## High-Level Embedding on Windows with Visual Studio

`JULIA_DIR` 환경 변수가 설정되지 않은 경우, Visual Studio를 시작하기 전에 시스템 패널을 사용하여 추가하십시오. `JULIA_DIR` 아래의 `bin` 폴더는 시스템 PATH에 있어야 합니다.

Visual Studio를 열고 새로운 콘솔 애플리케이션 프로젝트를 생성하는 것으로 시작합니다. 'stdafx.h' 헤더 파일을 열고, 끝에 다음 줄을 추가합니다:

```c
#include <julia.h>
```

그런 다음 프로젝트의 main() 함수를 이 코드로 교체하세요:

```c
int main(int argc, char *argv[])
{
    /* required: setup the Julia context */
    jl_init();

    /* run Julia commands */
    jl_eval_string("print(sqrt(2.0))");

    /* strongly recommended: notify Julia that the
         program is about to terminate. this allows
         Julia time to cleanup pending write requests
         and run all finalizers
    */
    jl_atexit_hook(0);
    return 0;
}
```

다음 단계는 Julia 포함 파일과 라이브러리를 찾기 위해 프로젝트를 설정하는 것입니다. Julia 설치가 32비트인지 64비트인지 아는 것이 중요합니다. 진행하기 전에 Julia 설치와 일치하지 않는 플랫폼 구성을 제거하십시오.

프로젝트 속성 대화 상자를 사용하여 `C/C++` | `일반`으로 이동한 다음 추가 포함 디렉터리 속성에 `$(JULIA_DIR)\include\julia\`를 추가합니다. 그런 다음 `링커` | `일반` 섹션으로 이동하여 추가 라이브러리 디렉터리 속성에 `$(JULIA_DIR)\lib`를 추가합니다. 마지막으로 `링커` | `입력` 아래에서 라이브러리 목록에 `libjulia.dll.a;libopenlibm.dll.a;`를 추가합니다.

이 시점에서 프로젝트는 빌드되고 실행되어야 합니다.

## Converting Types

실제 애플리케이션은 표현식을 실행할 뿐만 아니라 호스트 프로그램에 값을 반환해야 합니다. `jl_eval_string`은 힙에 할당된 Julia 객체에 대한 포인터인 `jl_value_t*`를 반환합니다. [`Float64`](@ref)와 같은 간단한 데이터 유형을 이와 같은 방식으로 저장하는 것을 `boxing`이라고 하며, 저장된 원시 데이터를 추출하는 것을 `unboxing`이라고 합니다. 2의 제곱근을 계산하고 C에서 결과를 다시 읽어오는 개선된 샘플 프로그램의 본문에는 이제 다음 코드가 포함되어 있습니다:

```c
jl_value_t *ret = jl_eval_string("sqrt(2.0)");

if (jl_typeis(ret, jl_float64_type)) {
    double ret_unboxed = jl_unbox_float64(ret);
    printf("sqrt(2.0) in C: %e \n", ret_unboxed);
}
else {
    printf("ERROR: unexpected return type from sqrt(::Float64)\n");
}
```

`ret`가 특정 Julia 타입인지 확인하기 위해 `jl_isa`, `jl_typeis` 또는 `jl_is_...` 함수를 사용할 수 있습니다. Julia 셸에 `typeof(sqrt(2.0))`를 입력하면 반환 타입이 [`Float64`](@ref) (`C`의 `double`)임을 확인할 수 있습니다. 위 코드 스니펫에서 박스된 Julia 값을 C double로 변환하기 위해 `jl_unbox_float64` 함수가 사용됩니다.

상응하는 `jl_box_...` 함수는 반대 방향으로 변환하는 데 사용됩니다:

```c
jl_value_t *a = jl_box_float64(3.0);
jl_value_t *b = jl_box_float32(3.0f);
jl_value_t *c = jl_box_int32(3);
```

다음에서 볼 수 있듯이, 특정 인수로 Julia 함수를 호출하려면 박싱이 필요합니다.

## Calling Julia Functions

`jl_eval_string`는 C가 Julia 표현식의 결과를 얻을 수 있게 해주지만, C에서 계산된 인수를 Julia로 전달하는 것은 허용하지 않습니다. 이를 위해서는 `jl_call`을 사용하여 Julia 함수를 직접 호출해야 합니다:

```c
jl_function_t *func = jl_get_function(jl_base_module, "sqrt");
jl_value_t *argument = jl_box_float64(2.0);
jl_value_t *ret = jl_call1(func, argument);
```

첫 번째 단계에서는 `jl_get_function`을 호출하여 Julia 함수 `sqrt`에 대한 핸들을 가져옵니다. `jl_get_function`에 전달되는 첫 번째 인수는 `sqrt`가 정의된 `Base` 모듈에 대한 포인터입니다. 그런 다음, 더블 값을 `jl_box_float64`를 사용하여 박싱합니다. 마지막 단계에서는 `jl_call1`을 사용하여 함수를 호출합니다. 인수의 수에 따라 편리하게 처리할 수 있도록 `jl_call0`, `jl_call2`, 및 `jl_call3` 함수도 존재합니다. 더 많은 인수를 전달하려면 `jl_call`을 사용하세요:

```
jl_value_t *jl_call(jl_function_t *f, jl_value_t **args, int32_t nargs)
```

두 번째 인수 `args`는 `jl_value_t*` 인수의 배열이며, `nargs`는 인수의 수입니다.

또한, 줄리아 함수를 호출하는 대안적이고 아마도 더 간단한 방법이 있으며, 그것은 [`@cfunction`](@ref)를 통해서입니다. `@cfunction`을 사용하면 줄리아 측에서 타입 변환을 수행할 수 있으며, 이는 일반적으로 C 측에서 수행하는 것보다 더 쉽습니다. 위의 `sqrt` 예제는 `@cfunction`을 사용하여 다음과 같이 작성됩니다:

```c
double (*sqrt_jl)(double) = jl_unbox_voidpointer(jl_eval_string("@cfunction(sqrt, Float64, (Float64,))"));
double ret = sqrt_jl(2.0);
```

여기서 우리는 먼저 Julia에서 C 호출 가능 함수를 정의하고, 그 함수 포인터를 추출한 다음, 최종적으로 호출하는 방법을 설명합니다. 고급 언어에서 타입 변환을 수행함으로써 단순화할 뿐만 아니라, `@cfunction` 포인터를 통해 Julia 함수를 호출하면 `jl_call`에 의해 요구되는 동적 디스패치 오버헤드를 제거할 수 있으며(모든 인수가 "박스화"됨), 성능은 네이티브 C 함수 포인터와 동등해야 합니다.

## Memory Management

우리가 보았듯이, Julia 객체는 C에서 `jl_value_t*` 유형의 포인터로 표현됩니다. 이는 이러한 객체를 해제하는 책임이 누구에게 있는지를 질문하게 만듭니다.

일반적으로 Julia 객체는 가비지 컬렉터(GC)에 의해 해제되지만, GC는 C에서 Julia 값에 대한 참조를 보유하고 있다는 것을 자동으로 알지 못합니다. 이는 GC가 객체를 해제하여 포인터를 무효화할 수 있음을 의미합니다.

GC는 새로운 Julia 객체가 할당될 때만 실행됩니다. `jl_box_float64`와 같은 호출은 할당을 수행하지만, 할당은 Julia 코드 실행 중 언제든지 발생할 수 있습니다.

Julia를 임베드하는 코드를 작성할 때, 일반적으로 `jl_...` 호출 사이에 `jl_value_t*` 값을 사용하는 것은 안전합니다(가비지 컬렉터는 이러한 호출에 의해만 트리거됩니다). 그러나 값이 `jl_...` 호출을 생존할 수 있도록 하려면, 여전히 Julia [root](https://www.cs.purdue.edu/homes/hosking/690M/p611-fenichel.pdf) 값에 대한 참조를 보유하고 있음을 Julia에 알려야 합니다. 이를 "GC 루팅"이라고 합니다. 값을 루팅하면 가비지 컬렉터가 이 값을 사용되지 않는 것으로 잘못 식별하고 해당 값을 지원하는 메모리를 해제하지 않도록 보장합니다. 이는 `JL_GC_PUSH` 매크로를 사용하여 수행할 수 있습니다:

```c
jl_value_t *ret = jl_eval_string("sqrt(2.0)");
JL_GC_PUSH1(&ret);
// Do something with ret
JL_GC_POP();
```

`JL_GC_POP` 호출은 이전 `JL_GC_PUSH`에 의해 설정된 참조를 해제합니다. `JL_GC_PUSH`는 C 스택에 참조를 저장하므로, 스코프를 벗어나기 전에 반드시 `JL_GC_POP`과 정확히 쌍을 이루어야 합니다. 즉, 함수가 반환되기 전에 또는 제어 흐름이 `JL_GC_PUSH`가 호출된 블록을 벗어나기 전에 이루어져야 합니다.

여러 Julia 값을 한 번에 푸시할 수 있습니다. `JL_GC_PUSH2`에서 `JL_GC_PUSH6` 매크로를 사용하세요:

```
JL_GC_PUSH2(&ret1, &ret2);
// ...
JL_GC_PUSH6(&ret1, &ret2, &ret3, &ret4, &ret5, &ret6);
```

배열의 Julia 값을 푸시하려면 `JL_GC_PUSHARGS` 매크로를 사용할 수 있으며, 다음과 같이 사용할 수 있습니다:

```c
jl_value_t **args;
JL_GC_PUSHARGS(args, 2); // args can now hold 2 `jl_value_t*` objects
args[0] = some_value;
args[1] = some_other_value;
// Do something with args (e.g. call jl_... functions)
JL_GC_POP();
```

각 범위는 `JL_GC_PUSH*`에 대한 호출이 하나만 있어야 하며, 단일 `JL_GC_POP` 호출과 쌍을 이루어야 합니다. 루팅하려는 모든 필요한 변수를 단일 호출로 `JL_GC_PUSH*`에 푸시할 수 없거나, 푸시해야 할 변수가 6개를 초과하고 인수 배열을 사용하는 것이 옵션이 아닐 경우, 내부 블록을 사용할 수 있습니다:

```c
jl_value_t *ret1 = jl_eval_string("sqrt(2.0)");
JL_GC_PUSH1(&ret1);
jl_value_t *ret2 = 0;
{
    jl_function_t *func = jl_get_function(jl_base_module, "exp");
    ret2 = jl_call1(func, ret1);
    JL_GC_PUSH1(&ret2);
    // Do something with ret2.
    JL_GC_POP();    // This pops ret2.
}
JL_GC_POP();    // This pops ret1.
```

`jl_value_t*` 값을 `JL_GC_PUSH*`를 호출하기 전에 유효하게 가질 필요는 없다는 점에 유의하세요. 여러 개의 값을 `NULL`로 초기화한 후, 이를 `JL_GC_PUSH*`에 전달하고 실제 Julia 값을 생성하는 것은 괜찮습니다. 예를 들어:

```
jl_value_t *ret1 = NULL, *ret2 = NULL;
JL_GC_PUSH2(&ret1, &ret2);
ret1 = jl_eval_string("sqrt(2.0)");
ret2 = jl_eval_string("sqrt(3.0)");
// Use ret1 and ret2
JL_GC_POP();
```

변수가 함수(또는 블록 범위) 사이에서 포인터를 유지해야 하는 경우, `JL_GC_PUSH*`를 사용할 수 없습니다. 이 경우, Julia 전역 범위에서 변수에 대한 참조를 생성하고 유지해야 합니다. 이를 달성하는 간단한 방법은 참조를 보유하고 GC에 의한 메모리 해제를 방지하는 전역 `IdDict`를 사용하는 것입니다. 그러나 이 방법은 변경 가능한 타입에 대해서만 제대로 작동합니다.

```c
// This functions shall be executed only once, during the initialization.
jl_value_t* refs = jl_eval_string("refs = IdDict()");
jl_function_t* setindex = jl_get_function(jl_base_module, "setindex!");

...

// `var` is the variable we want to protect between function calls.
jl_value_t* var = 0;

...

// `var` is a `Vector{Float64}`, which is mutable.
var = jl_eval_string("[sqrt(2.0); sqrt(4.0); sqrt(6.0)]");

// To protect `var`, add its reference to `refs`.
jl_call3(setindex, refs, var, var);
```

변수가 불변이면, `IdDict`에 푸시되기 전에 동등한 가변 컨테이너 또는 바람직하게는 `RefValue{Any}`로 감싸야 합니다. 이 접근 방식에서는 컨테이너가 C 코드를 사용하여 생성되거나 채워져야 하며, 예를 들어 `jl_new_struct` 함수를 사용할 수 있습니다. 컨테이너가 `jl_call*`에 의해 생성되면, C 코드에서 사용될 포인터를 다시 로드해야 합니다.

```c
// This functions shall be executed only once, during the initialization.
jl_value_t* refs = jl_eval_string("refs = IdDict()");
jl_function_t* setindex = jl_get_function(jl_base_module, "setindex!");
jl_datatype_t* reft = (jl_datatype_t*)jl_eval_string("Base.RefValue{Any}");

...

// `var` is the variable we want to protect between function calls.
jl_value_t* var = 0;

...

// `var` is a `Float64`, which is immutable.
var = jl_eval_string("sqrt(2.0)");

// Protect `var` until we add its reference to `refs`.
JL_GC_PUSH1(&var);

// Wrap `var` in `RefValue{Any}` and push to `refs` to protect it.
jl_value_t* rvar = jl_new_struct(reft, var);
JL_GC_POP();

jl_call3(setindex, refs, rvar, rvar);
```

GC는 `delete!` 함수를 사용하여 `refs`에서 변수에 대한 참조를 제거함으로써 변수를 해제할 수 있습니다. 단, 변수에 대한 다른 참조가 어디에도 남아 있지 않아야 합니다:

```c
jl_function_t* delete = jl_get_function(jl_base_module, "delete!");
jl_call2(delete, refs, rvar);
```

매우 간단한 경우의 대안으로, `Vector{Any}` 유형의 전역 컨테이너를 생성하고 필요할 때 그로부터 요소를 가져오거나, 포인터당 하나의 전역 변수를 생성하는 것도 가능합니다.

```c
jl_module_t *mod = jl_main_module;
jl_sym_t *var = jl_symbol("var");
jl_binding_t *bp = jl_get_binding_wr(mod, var, 1);
jl_checked_assignment(bp, mod, var, val);
```

### Updating fields of GC-managed objects

가비지 수집기는 또한 모든 구세대 객체가 젊은 세대 객체를 가리키고 있다는 가정 하에 작동합니다. 이 가정을 깨는 포인터가 업데이트될 때마다 `jl_gc_wb` (쓰기 장벽) 함수를 사용하여 수집기에 신호를 보내야 합니다.

```c
jl_value_t *parent = some_old_value, *child = some_young_value;
((some_specific_type*)parent)->field = child;
jl_gc_wb(parent, child);
```

일반적으로 런타임에 어떤 값이 오래될지를 예측하는 것은 불가능하므로, 쓰기 장벽은 모든 명시적 저장 후에 삽입되어야 합니다. 주목할 만한 예외는 `parent` 객체가 방금 할당되었고 그 이후로 가비지 컬렉션이 실행되지 않은 경우입니다. 대부분의 `jl_...` 함수는 때때로 가비지 컬렉션을 호출할 수 있다는 점에 유의하십시오.

쓰기 장벽은 데이터를 직접 업데이트할 때 포인터 배열에도 필요합니다. `jl_array_ptr_set`를 호출하는 것이 일반적으로 훨씬 선호됩니다. 그러나 직접 업데이트도 가능합니다. 예를 들어:

```c
jl_array_t *some_array = ...; // e.g. a Vector{Any}
void **data = jl_array_data(some_array, void*);
jl_value_t *some_value = ...;
data[0] = some_value;
jl_gc_wb(jl_array_owner(some_array), some_value);
```

### Controlling the Garbage Collector

GC를 제어하는 몇 가지 함수가 있습니다. 일반적인 사용 사례에서는 이러한 함수가 필요하지 않습니다.

| Function             | Description                                  |
|:-------------------- |:-------------------------------------------- |
| `jl_gc_collect()`    | Force a GC run                               |
| `jl_gc_enable(0)`    | Disable the GC, return previous state as int |
| `jl_gc_enable(1)`    | Enable the GC,  return previous state as int |
| `jl_gc_is_enabled()` | Return current state as int                  |

## Working with Arrays

줄리아와 C는 배열 데이터를 복사하지 않고 공유할 수 있습니다. 다음 예제는 이것이 어떻게 작동하는지를 보여줄 것입니다.

Julia 배열은 C에서 `jl_array_t*` 데이터 타입으로 표현됩니다. 기본적으로 `jl_array_t`는 다음을 포함하는 구조체입니다:

  * 데이터 타입에 대한 정보
  * 데이터 블록에 대한 포인터
  * 배열의 크기에 대한 정보

간단하게 유지하기 위해, 1D 배열로 시작합니다. 길이가 10인 Float64 요소를 포함하는 배열을 생성하는 방법은 다음과 같습니다:

```c
jl_value_t* array_type = jl_apply_array_type((jl_value_t*)jl_float64_type, 1);
jl_array_t* x          = jl_alloc_array_1d(array_type, 10);
```

대안으로, 이미 배열을 할당한 경우 그 데이터 주위에 얇은 래퍼를 생성할 수 있습니다:

```c
double *existingArray = (double*)malloc(sizeof(double)*10);
jl_array_t *x = jl_ptr_to_array_1d(array_type, existingArray, 10, 0);
```

마지막 인자는 Julia가 데이터의 소유권을 가져야 하는지를 나타내는 불리언입니다. 이 인자가 0이 아니면, GC는 배열이 더 이상 참조되지 않을 때 데이터 포인터에 대해 `free`를 호출합니다.

`x`의 데이터에 접근하기 위해 `jl_array_data`를 사용할 수 있습니다:

```c
double *xData = jl_array_data(x, double);
```

이제 배열을 채울 수 있습니다:

```c
for (size_t i = 0; i < jl_array_nrows(x); i++)
    xData[i] = i;
```

이제 `x`에 제자리 연산을 수행하는 Julia 함수를 호출해 보겠습니다:

```c
jl_function_t *func = jl_get_function(jl_base_module, "reverse!");
jl_call1(func, (jl_value_t*)x);
```

배열을 출력함으로써 `x`의 요소들이 이제 반전되었음을 확인할 수 있습니다.

### Accessing Returned Arrays

만약 Julia 함수가 배열을 반환하면, `jl_eval_string` 및 `jl_call`의 반환 값은 `jl_array_t*`로 캐스팅될 수 있습니다:

```c
jl_function_t *func  = jl_get_function(jl_base_module, "reverse");
jl_array_t *y = (jl_array_t*)jl_call1(func, (jl_value_t*)x);
```

이제 `y`의 내용은 이전과 같이 `jl_array_data`를 사용하여 접근할 수 있습니다. 항상 사용 중일 때 배열에 대한 참조를 유지하는 것을 잊지 마세요.

### Multidimensional Arrays

줄리아의 다차원 배열은 메모리에 열 우선 순서로 저장됩니다. 다음은 2D 배열을 생성하고 그 속성에 접근하는 코드입니다:

```c
// Create 2D array of float64 type
jl_value_t *array_type = jl_apply_array_type((jl_value_t*)jl_float64_type, 2);
int dims[] = {10,5};
jl_array_t *x  = jl_alloc_array_nd(array_type, dims, 2);

// Get array pointer
double *p = jl_array_data(x, double);
// Get number of dimensions
int ndims = jl_array_ndims(x);
// Get the size of the i-th dim
size_t size0 = jl_array_dim(x,0);
size_t size1 = jl_array_dim(x,1);

// Fill array with data
for(size_t i=0; i<size1; i++)
    for(size_t j=0; j<size0; j++)
        p[j + size0*i] = i + j;
```

주목할 점은 Julia 배열이 1 기반 인덱싱을 사용하는 반면, C API는 0 기반 인덱싱을 사용한다는 것입니다(예: `jl_array_dim` 호출 시). 이는 관용적인 C 코드로 읽히기 위함입니다.

## Exceptions

Julia 코드는 예외를 발생시킬 수 있습니다. 예를 들어, 다음을 고려해 보세요:

```c
jl_eval_string("this_function_does_not_exist()");
```

이 호출은 아무것도 하지 않는 것처럼 보일 것입니다. 그러나 예외가 발생했는지 확인하는 것은 가능합니다:

```c
if (jl_exception_occurred())
    printf("%s \n", jl_typeof_str(jl_exception_occurred()));
```

만약 예외를 지원하는 언어(예: Python, C#, C++)에서 Julia C API를 사용하고 있다면, 각 `libjulia` 호출을 예외가 발생했는지 확인하는 함수로 감싸고, 그런 다음 호스트 언어에서 예외를 다시 발생시키는 것이 합리적입니다.

### Throwing Julia Exceptions

줄리아 호출 가능 함수를 작성할 때, 인수를 검증하고 오류를 나타내기 위해 예외를 발생시키는 것이 필요할 수 있습니다. 일반적인 타입 검사는 다음과 같습니다:

```c
if (!jl_typeis(val, jl_float64_type)) {
    jl_type_error(function_name, (jl_value_t*)jl_float64_type, val);
}
```

일반 예외는 다음 함수를 사용하여 발생시킬 수 있습니다:

```c
void jl_error(const char *str);
void jl_errorf(const char *fmt, ...);
```

`jl_error`는 C 문자열을 받고, `jl_errorf`는 `printf`처럼 호출됩니다:

```c
jl_errorf("argument x = %d is too large", x);
```

이 예제에서 `x`는 정수로 가정됩니다.

### Thread-safety

일반적으로, Julia C API는 완전히 스레드 안전하지 않습니다. 다중 스레드 애플리케이션에 Julia를 임베드할 때는 다음 제한 사항을 위반하지 않도록 주의해야 합니다:

  * `jl_init()`는 애플리케이션 생애 주기에서 한 번만 호출될 수 있습니다. `jl_atexit_hook()`도 마찬가지이며, `jl_init()` 이후에만 호출될 수 있습니다.
  * `jl_...()` API 함수는 `jl_init()`가 호출된 스레드에서만 호출할 수 있으며, *또는 Julia 런타임에 의해 시작된 스레드에서 호출할 수 있습니다*. 사용자 시작 스레드에서 Julia API 함수를 호출하는 것은 지원되지 않으며, 정의되지 않은 동작 및 충돌을 초래할 수 있습니다.

위의 두 번째 조건은 Julia에 의해 시작되지 않은 스레드에서 `jl_...()` 함수를 안전하게 호출할 수 없음을 의미합니다 (예외는 `jl_init()`를 호출하는 스레드입니다). 예를 들어, 다음은 지원되지 않으며 대부분 세그멘테이션 오류가 발생할 것입니다:

```c
void *func(void*)
{
    // Wrong, jl_eval_string() called from thread that was not started by Julia
    jl_eval_string("println(Threads.threadid())");
    return NULL;
}

int main()
{
    pthread_t t;

    jl_init();

    // Start a new thread
    pthread_create(&t, NULL, func, NULL);
    pthread_join(t, NULL);

    jl_atexit_hook(0);
}
```

대신, 동일한 사용자 생성 스레드에서 모든 Julia 호출을 수행하면 작동합니다:

```c
void *func(void*)
{
    // Okay, all jl_...() calls from the same thread,
    // even though it is not the main application thread
    jl_init();
    jl_eval_string("println(Threads.threadid())");
    jl_atexit_hook(0);
    return NULL;
}

int main()
{
    pthread_t t;
    // Create a new thread, which runs func()
    pthread_create(&t, NULL, func, NULL);
    pthread_join(t, NULL);
}
```

Julia 자체에서 시작된 스레드에서 Julia C API를 호출하는 예:

```c
#include <julia/julia.h>
JULIA_DEFINE_FAST_TLS

double c_func(int i)
{
    printf("[C %08x] i = %d\n", pthread_self(), i);

    // Call the Julia sqrt() function to compute the square root of i, and return it
    jl_function_t *sqrt = jl_get_function(jl_base_module, "sqrt");
    jl_value_t* arg = jl_box_int32(i);
    double ret = jl_unbox_float64(jl_call1(sqrt, arg));

    return ret;
}

int main()
{
    jl_init();

    // Define a Julia function func() that calls our c_func() defined in C above
    jl_eval_string("func(i) = ccall(:c_func, Float64, (Int32,), i)");

    // Call func() multiple times, using multiple threads to do so
    jl_eval_string("println(Threads.threadpoolsize())");
    jl_eval_string("use(i) = println(\"[J $(Threads.threadid())] i = $(i) -> $(func(i))\")");
    jl_eval_string("Threads.@threads for i in 1:5 use(i) end");

    jl_atexit_hook(0);
}
```

이 코드를 2개의 Julia 스레드로 실행하면 다음과 같은 출력이 나타납니다(참고: 출력은 실행 및 시스템에 따라 달라질 수 있습니다):

```sh
$ JULIA_NUM_THREADS=2 ./thread_example
2
[C 3bfd9c00] i = 1
[C 23938640] i = 4
[J 1] i = 1 -> 1.0
[C 3bfd9c00] i = 2
[J 1] i = 2 -> 1.4142135623730951
[C 3bfd9c00] i = 3
[J 2] i = 4 -> 2.0
[C 23938640] i = 5
[J 1] i = 3 -> 1.7320508075688772
[J 2] i = 5 -> 2.23606797749979
```

보시다시피, Julia 스레드 1은 pthread ID 3bfd9c00에 해당하고, Julia 스레드 2는 ID 23938640에 해당하여 실제로 C 수준에서 여러 스레드가 사용되고 있음을 보여주며, 이러한 스레드에서 Julia C API 루틴을 안전하게 호출할 수 있음을 나타냅니다.
