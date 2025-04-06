# [Scope of Variables](@id scope-of-variables)

변수의 *범위*는 변수가 접근 가능한 코드의 영역입니다. 변수 범위는 변수 이름 충돌을 피하는 데 도움이 됩니다. 이 개념은 직관적입니다: 두 함수 모두 `x`라는 이름의 인수를 가질 수 있지만 두 `x`는 같은 것을 참조하지 않습니다. 마찬가지로, 서로 다른 코드 블록이 같은 이름을 사용하더라도 같은 것을 참조하지 않는 경우가 많습니다. 같은 변수 이름이 같은 것을 참조하는지 여부에 대한 규칙을 범위 규칙이라고 하며, 이 섹션에서는 이를 자세히 설명합니다.

언어의 특정 구성 요소는 *스코프 블록*을 도입하는데, 이는 특정 변수 집합의 스코프가 될 수 있는 코드 영역입니다. 변수의 스코프는 임의의 소스 라인 집합이 될 수 없으며, 항상 이러한 블록 중 하나와 일치해야 합니다. Julia에는 두 가지 주요 스코프 유형이 있습니다: *전역 스코프*와 *지역 스코프*. 후자는 중첩될 수 있습니다. 또한 Julia에서는 "하드 스코프"를 도입하는 구성 요소와 "소프트 스코프"만 도입하는 구성 요소 간에 구분이 있으며, 이는 [shadowing](https://en.wikipedia.org/wiki/Variable_shadowing)라는 동일한 이름의 전역 변수가 허용되는지 여부에 영향을 미칩니다.

### [Scope constructs](@id man-scope-table)

범위를 도입하는 구조물은 다음과 같습니다:

| Construct                                                                        | Scope type   | Allowed within |
|:-------------------------------------------------------------------------------- |:------------ |:-------------- |
| [`module`](@ref), [`baremodule`](@ref)                                           | global       | global         |
| [`struct`](@ref)                                                                 | local (soft) | global         |
| [`for`](@ref), [`while`](@ref), [`try`](@ref try)                                | local (soft) | global, local  |
| [`macro`](@ref)                                                                  | local (hard) | global         |
| functions, [`do`](@ref) blocks, [`let`](@ref) blocks, comprehensions, generators | local (hard) | global, local  |

이 표에서 눈에 띄게 빠진 것은 [begin blocks](@ref man-compound-expressions)와 [if blocks](@ref man-conditional-evaluation)으로, 이들은 *새로운* 스코프를 도입하지 않습니다. 세 가지 유형의 스코프는 다소 다른 규칙을 따르며, 이는 아래에서 설명될 것입니다.

줄리아는 [lexical scoping](https://en.wikipedia.org/wiki/Scope_(computer_science)#Lexical_scope_vs._dynamic_scope)를 사용합니다. 이는 함수의 범위가 호출자의 범위가 아니라 함수가 정의된 범위에서 상속됨을 의미합니다. 예를 들어, 다음 코드에서 `foo` 내부의 `x`는 모듈 `Bar`의 전역 범위에 있는 `x`를 참조합니다:

```jldoctest moduleBar
julia> module Bar
           x = 1
           foo() = x
       end;
```

그리고 `foo`가 사용되는 범위에 `x`가 없습니다:

```jldoctest moduleBar
julia> import .Bar

julia> x = -1;

julia> Bar.foo()
1
```

따라서 *어휘적 범위*는 특정 코드 조각에서 변수가 참조하는 것이 그것이 나타나는 코드만으로 유추될 수 있으며 프로그램의 실행 방식에 의존하지 않음을 의미합니다. 다른 범위 안에 중첩된 범위는 자신이 포함된 모든 외부 범위의 변수를 "볼" 수 있습니다. 반면 외부 범위는 내부 범위의 변수를 볼 수 없습니다.

## Global Scope

각 모듈은 다른 모든 모듈의 전역 범위와는 별개의 새로운 전역 범위를 도입합니다. 즉, 포괄적인 전역 범위는 존재하지 않습니다. 모듈은 [using or import](@ref modules) 문을 통해 또는 점 표기법을 사용한 한정된 접근을 통해 다른 모듈의 변수를 자신의 범위로 도입할 수 있습니다. 즉, 각 모듈은 이름과 값을 연결하는 일급 데이터 구조이자 소위 *네임스페이스*입니다.

최상위 표현식에 `local` 키워드를 사용한 변수 선언이 포함되어 있으면, 해당 변수는 그 표현식 외부에서 접근할 수 없습니다. 표현식 내부의 변수는 동일한 이름의 전역 변수에 영향을 미치지 않습니다. 예를 들어, 최상위에서 `begin` 또는 `if` 블록 내에 `local x`를 선언하는 것입니다:

```jldoctest
julia> x = 1
       begin
           local x = 0
           @show x
       end
       @show x;
x = 0
x = 1
```

모듈 `Main`의 전역 범위에 대화형 프롬프트(즉, REPL)가 있음을 유의하세요.

## [Local Scope](@id local-scope)

대부분의 코드 블록에 의해 새로운 로컬 스코프가 도입됩니다(완전한 목록은 위의 [table](@ref man-scope-table)를 참조하십시오). 이러한 블록이 다른 로컬 스코프 내부에 구문적으로 중첩되어 있는 경우, 생성된 스코프는 그 안에 나타나는 모든 로컬 스코프 내부에 중첩되며, 이는 궁극적으로 코드가 평가되는 모듈의 글로벌 스코프 내부에 중첩됩니다. 외부 스코프의 변수는 포함된 모든 스코프에서 볼 수 있습니다. 즉, 내부 스코프에서 읽고 쓸 수 있습니다. 단, 동일한 이름의 로컬 변수가 외부 변수의 동일한 이름을 "가리는" 경우는 제외됩니다. 이는 외부 로컬이 내부 블록 아래에 텍스트적으로 선언된 경우에도 해당됩니다. 변수가 주어진 스코프에서 "존재한다"고 말할 때, 이는 해당 이름의 변수가 현재 스코프가 중첩된 모든 스코프, 현재 스코프를 포함하여 존재한다는 것을 의미합니다.

일부 프로그래밍 언어는 변수를 사용하기 전에 명시적으로 선언해야 합니다. 명시적 선언은 Julia에서도 작동합니다: 어떤 로컬 범위에서 `local x`를 작성하면, 외부 범위에 이미 `x`라는 변수가 있든 없든 관계없이 해당 범위에 새로운 로컬 변수를 선언합니다. 그러나 이렇게 각 새로운 변수를 선언하는 것은 다소 장황하고 지루하므로, Julia는 다른 많은 언어와 마찬가지로 존재하지 않는 변수 이름에 할당하는 것을 해당 변수를 암묵적으로 선언하는 것으로 간주합니다. 현재 범위가 전역이면 새로운 변수는 전역이고, 현재 범위가 로컬이면 새로운 변수는 가장 안쪽 로컬 범위에 로컬이며 해당 범위 내에서만 보입니다. 기존 로컬에 할당하면 *항상* 해당 기존 로컬을 업데이트합니다: 중첩된 범위에서 `local` 키워드를 사용하여 새로운 로컬을 명시적으로 선언해야만 로컬을 가릴 수 있습니다. 특히, 이는 내부 함수에서 할당된 변수에 적용되며, 이는 변수의 명시적 비로컬 선언이 없는 한 내부 함수에서의 할당이 새로운 로컬을 생성하는 Python에서 오는 사용자에게는 놀라울 수 있습니다.

대부분 이것은 꽤 직관적이지만, 직관적으로 행동하는 많은 것들과 마찬가지로, 세부 사항은 누군가가 순진하게 상상하는 것보다 더 미묘합니다.

`x = <value>`가 로컬 범위에서 발생할 때, Julia는 할당 표현식이 발생하는 위치와 그 위치에서 `x`가 이미 참조하는 것에 따라 표현식의 의미를 결정하기 위해 다음 규칙을 적용합니다:

1. **기존 로컬:** 만약 `x`가 *이미 로컬 변수*인 경우, 기존 로컬 `x`가 할당됩니다;
2. **하드 스코프:** 만약 `x`가 *이미 로컬 변수가 아닐 경우* 하드 스코프 구조(즉, `let` 블록, 함수 또는 매크로 본문, 컴프리헨션, 또는 제너레이터) 내에서 할당이 발생하면, 할당의 스코프 내에 새로운 로컬 변수 `x`가 생성됩니다;
3. **소프트 스코프:** 만약 `x`가 *이미 로컬 변수가 아닌 경우*이고 할당을 포함하는 모든 스코프 구조가 소프트 스코프(루프, `try`/`catch` 블록 또는 `struct` 블록)인 경우, 동작은 전역 변수 `x`가 정의되어 있는지 여부에 따라 달라집니다:

      * 전역 `x`가 *정의되지 않은* 경우, 할당의 범위 내에 새로운 지역 `x`가 생성됩니다;
      * 전역 `x`가 *정의되어* 있으면, 할당은 모호한 것으로 간주됩니다:

          * *비상호작용* 컨텍스트(파일, eval)에서는 모호성 경고가 출력되고 새로운 로컬이 생성됩니다;
          * *대화형* 컨텍스트(REPL, 노트북)에서 전역 변수 `x`가 할당됩니다.

비대화형 컨텍스트에서는 하드 스코프와 소프트 스코프의 동작이 동일하다는 점에 유의할 수 있습니다. 단, 암묵적으로 로컬 변수(즉, `local x`로 선언되지 않은 변수)가 글로벌 변수를 가릴 때 경고가 출력됩니다. 대화형 컨텍스트에서는 편의성을 위해 규칙이 더 복잡한 휴리스틱을 따릅니다. 이는 다음에 나오는 예제에서 자세히 다루어집니다.

이제 규칙을 알았으니 몇 가지 예제를 살펴보겠습니다. 각 예제는 새 REPL 세션에서 평가된다고 가정하므로 각 코드 블록에서 할당된 전역 변수만 존재합니다.

우리는 명확하고 간단한 상황으로 시작할 것입니다—이 경우 함수 본문 내의 하드 스코프에서의 할당, 이미 해당 이름의 지역 변수가 존재하지 않을 때입니다:

```jldoctest
julia> function greet()
           x = "hello" # new local
           println(x)
       end
greet (generic function with 1 method)

julia> greet()
hello

julia> x # global
ERROR: UndefVarError: `x` not defined in `Main`
```

`greet` 함수 내부에서 `x = "hello"` 할당은 `x`가 함수의 범위 내에서 새로운 지역 변수가 되도록 합니다. 두 가지 관련 사실이 있습니다: 할당이 지역 범위에서 발생하고, 기존의 지역 `x` 변수가 없습니다. `x`가 지역 변수이기 때문에, 전역에 `x`라는 이름이 있든 없든 상관 없습니다. 여기서 예를 들어, `greet`를 정의하고 호출하기 전에 `x = 123`을 정의합니다:

```jldoctest
julia> x = 123 # global
123

julia> function greet()
           x = "hello" # new local
           println(x)
       end
greet (generic function with 1 method)

julia> greet()
hello

julia> x # global
123
```

`greet`에서의 `x`는 지역적이기 때문에, `greet`를 호출해도 전역 `x`의 값(또는 그 부재)은 영향을 받지 않습니다. 하드 스코프 규칙은 전역에 `x`라는 이름이 존재하는지 여부에 상관하지 않습니다: 하드 스코프에서 `x`에 대한 할당은 지역적입니다(단, `x`가 전역으로 선언되지 않은 경우).

The next clear cut situation we'll consider is when there is already a local variable named `x`, in which case `x = <value>` always assigns to this existing local `x`. This is true whether the assignment occurs in the same local scope, an inner local scope in the same function body, or in the body of a function nested inside of another function, also known as a [closure](https://en.wikipedia.org/wiki/Closure_(computer_programming)).

우리는 `sum_to` 함수를 사용할 것입니다. 이 함수는 1부터 `n`까지의 정수의 합을 계산합니다.

```julia
function sum_to(n)
    s = 0 # new local
    for i = 1:n
        s = s + i # assign existing local
    end
    return s # same local
end
```

이전 예제와 마찬가지로, `sum_to`의 맨 위에서 `s`에 대한 첫 번째 할당은 `s`가 함수 본문 내의 새로운 지역 변수가 되도록 합니다. `for` 루프는 함수 범위 내에서 자체 내부 지역 범위를 가집니다. `s = s + i`가 발생하는 지점에서 `s`는 이미 지역 변수이므로, 할당은 새로운 지역 변수를 생성하는 대신 기존의 `s`를 업데이트합니다. REPL에서 `sum_to`를 호출하여 이를 테스트할 수 있습니다:

```jldoctest
julia> function sum_to(n)
           s = 0 # new local
           for i = 1:n
               s = s + i # assign existing local
           end
           return s # same local
       end
sum_to (generic function with 1 method)

julia> sum_to(10)
55

julia> s # global
ERROR: UndefVarError: `s` not defined in `Main`
```

`s`는 `sum_to` 함수에 국한되어 있으므로, 함수를 호출해도 전역 변수 `s`에는 영향을 미치지 않습니다. 또한 `for` 루프에서의 업데이트 `s = s + i`는 초기화 `s = 0`에 의해 생성된 동일한 `s`를 업데이트했음이 분명합니다. 따라서 1부터 10까지의 정수에 대한 올바른 합계인 55를 얻을 수 있습니다.

잠시 `for` 루프 본문이 자체 범위를 가진다는 사실을 살펴보겠습니다. 이를 위해 `sum_to_def`라는 약간 더 자세한 변형을 작성해 보겠습니다. 여기서 우리는 `s`를 업데이트하기 전에 `s + i`의 합을 변수 `t`에 저장합니다:

```jldoctest
julia> function sum_to_def(n)
           s = 0 # new local
           for i = 1:n
               t = s + i # new local `t`
               s = t # assign existing local `s`
           end
           return s, @isdefined(t)
       end
sum_to_def (generic function with 1 method)

julia> sum_to_def(10)
(55, false)
```

이 버전은 이전과 같이 `s`를 반환하지만, 또한 `@isdefined` 매크로를 사용하여 함수의 가장 바깥쪽 로컬 스코프에 `t`라는 이름의 로컬 변수가 정의되어 있는지 여부를 나타내는 불리언 값을 반환합니다. 보시다시피, `for` 루프 본문 외부에는 `t`가 정의되어 있지 않습니다. 이는 다시 하드 스코프 규칙 때문입니다: `t`에 대한 할당이 함수 내부에서 발생하므로, 이는 하드 스코프를 도입하고, 할당으로 인해 `t`는 나타나는 로컬 스코프, 즉 루프 본문 내부에서 새로운 로컬 변수가 됩니다. 만약 전역에 `t`라는 이름이 있다 하더라도, 하드 스코프 규칙은 전역 스코프의 어떤 것에도 영향을 받지 않습니다.

for 루프 본문의 지역 범위는 내부 함수의 지역 범위와 다르지 않다는 점에 유의하세요. 이는 루프 본문을 내부 헬퍼 함수 호출로 구현하여 동일한 방식으로 작동하도록 이 예제를 다시 작성할 수 있음을 의미합니다.

```jldoctest
julia> function sum_to_def_closure(n)
           function loop_body(i)
               t = s + i # new local `t`
               s = t # assign same local `s` as below
           end
           s = 0 # new local
           for i = 1:n
               loop_body(i)
           end
           return s, @isdefined(t)
       end
sum_to_def_closure (generic function with 1 method)

julia> sum_to_def_closure(10)
(55, false)
```

이 예시는 몇 가지 주요 사항을 설명합니다:

1. 내부 함수 스코프는 다른 중첩 로컬 스코프와 같습니다. 특히, 만약 변수가 내부 함수 외부에서 이미 로컬 변수라면, 내부 함수에서 그 변수에 값을 할당하면 외부 로컬 변수가 업데이트됩니다.
2. 외부 로컬의 정의가 업데이트되는 아래에서 발생하더라도 상관없습니다. 규칙은 동일하게 유지됩니다. 전체 외부 로컬 범위가 파싱되고 그 로컬이 결정된 후에야 내부 로컬 의미가 해결됩니다.

이 디자인은 일반적으로 내부 함수로 코드를 이동하거나 이동할 수 있음을 의미하며, 이는 클로저를 사용하는 언어의 여러 일반적인 관용구를 용이하게 합니다 (참조: [do blocks](@ref Do-Block-Syntax-for-Function-Arguments)).

더 모호한 사례로 넘어가 보겠습니다. 소프트 스코프 규칙에 의해 다루어지는 사례입니다. `greet`와 `sum_to_def` 함수의 본문을 소프트 스코프 컨텍스트로 추출하여 살펴보겠습니다. 먼저, `greet`의 본문을 하드가 아닌 소프트인 `for` 루프에 넣고 REPL에서 평가해 보겠습니다:

```jldoctest
julia> for i = 1:3
           x = "hello" # new local
           println(x)
       end
hello
hello
hello

julia> x
ERROR: UndefVarError: `x` not defined in `Main`
```

글로벌 `x`가 `for` 루프가 평가될 때 정의되지 않기 때문에, 소프트 스코프 규칙의 첫 번째 조항이 적용되어 `x`가 `for` 루프에 로컬로 생성되며, 따라서 루프가 실행된 후에도 글로벌 `x`는 정의되지 않은 상태로 남아 있습니다. 다음으로, 인수를 `n = 10`으로 고정하여 글로벌 스코프로 추출된 `sum_to_def`의 본체를 고려해 봅시다.

```julia
s = 0
for i = 1:10
    t = s + i
    s = t
end
s
@isdefined(t)
```

이 코드는 무엇을 하나요? 힌트: 속임수 질문입니다. 답은 "상황에 따라 다르다." 이 코드가 대화형으로 입력되면 함수 본문에서와 동일하게 동작합니다. 그러나 코드가 파일에 나타나면 모호성 경고를 출력하고 정의되지 않은 변수 오류를 발생시킵니다. 먼저 REPL에서 작동하는 모습을 살펴보겠습니다:

```jldoctest
julia> s = 0 # global
0

julia> for i = 1:10
           t = s + i # new local `t`
           s = t # assign global `s`
       end

julia> s # global
55

julia> @isdefined(t) # global
false
```

REPL은 루프 내에서의 할당이 전역 변수에 할당되는지 아니면 새로운 지역 변수를 생성하는지를 결정하여 함수 본체에 있는 것처럼 근사합니다. 해당 이름의 전역 변수가 정의되어 있으면 할당이 이를 업데이트합니다. 전역 변수가 존재하지 않으면 할당이 새로운 지역 변수를 생성합니다. 이 예제에서는 두 가지 경우를 모두 볼 수 있습니다:

  * 전역 이름 `t`가 없으므로 `t = s + i`는 `for` 루프에 국한된 새로운 `t`를 생성합니다;
  * 전역 변수 `s`가 있으므로 `s = t`는 그것에 할당합니다.

두 번째 사실은 루프의 실행이 `s`의 전역 값을 변경하는 이유이고, 첫 번째 사실은 루프가 실행된 후에도 `t`가 여전히 정의되지 않은 이유입니다. 이제 이 동일한 코드를 파일에 있는 것처럼 평가해 보겠습니다:

```jldoctest
julia> code = """
       s = 0 # global
       for i = 1:10
           t = s + i # new local `t`
           s = t # new local `s` with warning
       end
       s, # global
       @isdefined(t) # global
       """;

julia> include_string(Main, code)
┌ Warning: Assignment to `s` in soft scope is ambiguous because a global variable by the same name exists: `s` will be treated as a new local. Disambiguate by using `local s` to suppress this warning or `global s` to assign to the existing global variable.
└ @ string:4
ERROR: LoadError: UndefVarError: `s` not defined in local scope
```

여기서 우리는 [`include_string`](@ref)를 사용하여 `code`를 파일의 내용인 것처럼 평가합니다. 우리는 또한 `code`를 파일에 저장한 다음 그 파일에 대해 `include`를 호출할 수 있습니다. 결과는 동일할 것입니다. 보시다시피, 이것은 REPL에서 동일한 코드를 평가하는 것과는 매우 다르게 작동합니다. 여기서 무슨 일이 일어나고 있는지 살펴보겠습니다:

  * 전역 `s`는 루프가 평가되기 전에 값 `0`으로 정의됩니다.
  * 할당 `s = t`는 함수 본체나 다른 하드 스코프 구조 밖의 `for` 루프와 같은 소프트 스코프에서 발생합니다.
  * 따라서 소프트 스코프 규칙의 두 번째 조항이 적용되며, 할당이 모호하므로 경고가 발생합니다.
  * 실행이 계속되며, `s`는 `for` 루프 본문에 로컬로 설정됩니다.
  * `s`는 `for` 루프에 국한되므로 `t = s + i`가 평가될 때 정의되지 않아 오류가 발생합니다.
  * 평가는 거기서 멈추지만, 만약 `s`와 `@isdefined(t)`에 도달하면 `0`과 `false`를 반환할 것입니다.

이것은 범위의 몇 가지 중요한 측면을 보여줍니다: 범위 내에서 각 변수는 하나의 의미만 가질 수 있으며, 그 의미는 표현식의 순서와 관계없이 결정됩니다. 루프 내의 표현식 `s = t`의 존재는 `s`가 루프에 국한된다는 것을 의미하며, 이는 `t = s + i`의 오른쪽에 나타날 때도 국한된다는 것을 의미합니다. 비록 그 표현식이 먼저 나타나고 먼저 평가되더라도 말입니다. 루프의 첫 번째 줄에 있는 `s`는 전역일 수 있고 두 번째 줄에 있는 `s`는 지역일 수 있다고 상상할 수 있지만, 두 줄이 같은 범위 블록에 있기 때문에 이는 불가능합니다. 각 변수는 주어진 범위에서 하나의 의미만 가질 수 있습니다.

#### [On Soft Scope](@id on-soft-scope)

이제 모든 지역 범위 규칙을 다루었지만, 이 섹션을 마무리하기 전에 대화형 및 비대화형 컨텍스트에서 모호한 소프트 범위 사례가 다르게 처리되는 이유에 대해 몇 마디 언급해야 할 것 같습니다. 다음과 같은 두 가지 명백한 질문을 할 수 있습니다:

1. 왜 REPL처럼 어디서나 작동하지 않을까요?
2. 왜 모든 파일에서처럼 그냥 작동하지 않을까요? 그리고 경고를 건너뛰는 것은 어떨까요?

줄리아 ≤ 0.6에서는 모든 전역 스코프가 현재 REPL처럼 작동했습니다. 루프(또는 `try`/`catch`, 또는 `struct` 본문) 내에서 함수 본문(또는 `let` 블록 또는 컴프리헨션) 외부에서 `x = <value>`가 발생할 때, 전역 이름 `x`가 정의되어 있는지 여부에 따라 `x`가 루프에 국한되어야 하는지가 결정되었습니다. 이 동작은 함수 본문 내의 동작을 최대한 가깝게 근사하기 때문에 직관적이고 편리하다는 장점이 있습니다. 특히, 함수의 동작을 디버깅할 때 함수 본문과 REPL 간에 코드를 쉽게 이동할 수 있게 해줍니다. 그러나 몇 가지 단점이 있습니다. 첫째, 이는 꽤 복잡한 동작입니다. 수년 동안 많은 사람들이 이 동작에 혼란을 느끼고 복잡하고 설명하기 어렵다고 불평했습니다. 타당한 지적입니다. 둘째, 그리고 아마도 더 나쁜 점은 "대규모 프로그래밍"에 좋지 않다는 것입니다. 이렇게 한 곳에서 작은 코드 조각을 보면 무슨 일이 일어나고 있는지 꽤 명확합니다:

```julia
s = 0
for i = 1:10
    s += i
end
```

명백히 의도는 기존의 전역 변수 `s`를 수정하는 것입니다. 그 외에 어떤 의미가 있을 수 있겠습니까? 그러나 실제 코드가 항상 이렇게 짧거나 명확한 것은 아닙니다. 우리는 다음과 같은 코드가 실제로 자주 발생한다는 것을 발견했습니다:

```julia
x = 123

# much later
# maybe in a different file

for i = 1:10
    x = "hello"
    println(x)
end

# much later
# maybe in yet another file
# or maybe back in the first one where `x = 123`

y = x + 234
```

여기서 어떤 일이 일어나야 하는지는 훨씬 덜 명확합니다. `x + "hello"`가 메서드 오류이기 때문에, `x`가 `for` 루프에 국한되기를 의도했을 가능성이 높습니다. 그러나 런타임 값과 어떤 메서드가 존재하는지를 사용하여 변수의 범위를 결정할 수는 없습니다. Julia ≤ 0.6의 동작으로 인해, 누군가가 `for` 루프를 먼저 작성하고 잘 작동했지만, 나중에 다른 사람이 멀리 떨어진 새로운 전역 변수를 추가했을 때—아마도 다른 파일에서—코드의 의미가 갑자기 바뀌고 소음이 발생하거나, 더 나쁜 경우에는 조용히 잘못된 작업을 수행하게 되는 것이 특히 우려됩니다. 이러한 종류의 ["spooky action at a distance"](https://en.wikipedia.org/wiki/Action_at_a_distance_(computer_programming))는 좋은 프로그래밍 언어 설계가 방지해야 할 것입니다.

그래서 Julia 1.0에서는 범위 규칙을 단순화했습니다: 어떤 로컬 범위에서 이미 로컬 변수가 아닌 이름에 할당하면 새로운 로컬 변수가 생성됩니다. 이는 소프트 범위 개념을 완전히 제거하고, 불가사의한 행동의 가능성을 없앴습니다. 소프트 범위 제거로 인해 상당수의 버그를 발견하고 수정했으며, 이를 없애기로 한 선택이 정당화되었습니다. 그리고 많은 기쁨이 있었습니다! 음, 아니요, 사실 그렇지 않았습니다. 왜냐하면 일부 사람들은 이제 다음과 같이 작성해야 한다고 화를 냈기 때문입니다:

```julia
s = 0
for i = 1:10
    global s += i
end
```

그 안에 있는 `global` 주석 보이세요? 끔찍하네요. 분명히 이 상황은 용납될 수 없습니다. 하지만 진지하게, 이러한 종류의 최상위 코드에 `global`을 요구하는 데는 두 가지 주요 문제가 있습니다:

1. 함수 본문 안의 코드를 REPL에 복사하고 붙여넣어 디버깅하는 것이 더 이상 편리하지 않습니다. `global` 주석을 추가한 다음 다시 돌아가기 위해 이를 제거해야 합니다.
2. 초보자들은 `global` 없이 이런 종류의 코드를 작성하고, 그들의 코드가 왜 작동하지 않는지 전혀 알지 못합니다. 그들이 받는 오류는 `s`가 정의되지 않았다는 것이며, 이는 이 실수를 저지른 사람에게는 아무런 도움이 되지 않는 것처럼 보입니다.

Julia 1.5부터 이 코드는 REPL이나 Jupyter 노트북과 같은 대화형 컨텍스트에서 `global` 주석 없이 작동합니다(마치 Julia 0.6처럼) 그리고 파일 및 기타 비대화형 컨텍스트에서는 매우 직접적인 경고를 출력합니다:

> `s`에 대한 할당이 소프트 스코프에서 모호합니다. 같은 이름의 전역 변수가 존재하기 때문에 `s`는 새로운 로컬로 처리됩니다. 이 경고를 억제하려면 `local s`를 사용하여 모호성을 해소하거나, 기존 전역 변수에 할당하려면 `global s`를 사용하십시오.


이것은 두 가지 문제를 해결하면서 1.0 동작의 "대규모 프로그래밍" 이점을 유지합니다: 전역 변수는 멀리 떨어진 코드의 의미에 스푸키한 영향을 미치지 않습니다; REPL에서 복사-붙여넣기 디버깅이 작동하고 초보자들은 아무런 문제를 겪지 않습니다; 누군가 `global` 주석을 잊거나 부드러운 범위에서 로컬로 기존 전역 변수를 우연히 가리는 경우, 어차피 혼란스러울 수 있는 상황에서 그들은 명확한 경고를 받습니다.

이 디자인의 중요한 속성은 경고 없이 파일에서 실행되는 모든 코드가 새 REPL에서 동일한 방식으로 동작한다는 것입니다. 반대로, REPL 세션을 파일로 저장하고 REPL에서와 다르게 동작하면 경고가 발생합니다.

### Let Blocks

`let` 문은 새로운 *하드 스코프* 블록을 생성하고(위 참조) 실행될 때마다 새로운 변수 바인딩을 도입합니다. 변수는 즉시 할당될 필요는 없습니다:

```jldoctest
julia> var1 = let x
           for i in 1:5
               (i == 4) && (x = i; break)
           end
           x
       end
4
```

할당은 기존 값 위치에 새 값을 재할당할 수 있지만, `let`은 항상 새 위치를 생성합니다. 이 차이는 일반적으로 중요하지 않으며, 클로저를 통해 범위를 초과하여 생존하는 변수의 경우에만 감지할 수 있습니다. `let` 구문은 쉼표로 구분된 일련의 할당 및 변수 이름을 허용합니다:

```jldoctest
julia> x, y, z = -1, -1, -1;

julia> let x = 1, z
           println("x: $x, y: $y") # x is local variable, y the global
           println("z: $z") # errors as z has not been assigned yet but is local
       end
x: 1, y: -1
ERROR: UndefVarError: `z` not defined in local scope
```

할당은 순서대로 평가되며, 각 오른쪽 항은 왼쪽의 새로운 변수가 도입되기 전에 범위 내에서 평가됩니다. 따라서 `let x = x`와 같은 것을 작성하는 것이 의미가 있습니다. 두 `x` 변수는 서로 다르며 별도의 저장소를 가지고 있기 때문입니다. 다음은 `let`의 동작이 필요한 예입니다:

```jldoctest
julia> Fs = Vector{Any}(undef, 2); i = 1;

julia> while i <= 2
           Fs[i] = ()->i
           global i += 1
       end

julia> Fs[1]()
3

julia> Fs[2]()
3
```

여기서 우리는 변수 `i`를 반환하는 두 개의 클로저를 생성하고 저장합니다. 그러나 항상 동일한 변수 `i`이므로 두 클로저는 동일하게 동작합니다. `let`을 사용하여 `i`에 대한 새로운 바인딩을 생성할 수 있습니다:

```jldoctest
julia> Fs = Vector{Any}(undef, 2); i = 1;

julia> while i <= 2
           let i = i
               Fs[i] = ()->i
           end
           global i += 1
       end

julia> Fs[1]()
1

julia> Fs[2]()
2
```

`begin` 구문은 새로운 범위를 도입하지 않기 때문에, 새로운 바인딩을 즉시 생성하지 않고 새로운 범위 블록을 도입하기 위해 인수가 없는 `let`을 사용하는 것이 유용할 수 있습니다:

```jldoctest
julia> let
           local x = 1
           let
               local x = 2
           end
           x
       end
1
```

`let`이 새로운 스코프 블록을 도입하기 때문에, 내부 지역 변수 `x`는 외부 지역 변수 `x`와 다른 변수입니다. 이 특정 예제는 다음과 같습니다:

```jldoctest
julia> let x = 1
           let x = 2
           end
           x
       end
1
```

### Loops and Comprehensions

In loops and [comprehensions](@ref man-comprehensions), new variables introduced in their body scopes are freshly allocated for each loop iteration, as if the loop body were surrounded by a `let` block, as demonstrated by this example:

```jldoctest
julia> Fs = Vector{Any}(undef, 2);

julia> for j = 1:2
           Fs[j] = ()->j
       end

julia> Fs[1]()
1

julia> Fs[2]()
2
```

`for` 루프 또는 이해(comprehension) 반복 변수는 항상 새로운 변수입니다:

```julia-repl enable_doctest_when_deprecation_warning_is_removed
julia> function f()
           i = 0
           for i = 1:3
               # empty
           end
           return i
       end;

julia> f()
0
```

그러나 기존의 지역 변수를 반복 변수로 재사용하는 것이 가끔 유용할 수 있습니다. 이는 `outer` 키워드를 추가하여 편리하게 수행할 수 있습니다:

```jldoctest
julia> function f()
           i = 0
           for outer i = 1:3
               # empty
           end
           return i
       end;

julia> f()
3
```

## Constants

변수의 일반적인 용도는 특정하고 변하지 않는 값에 이름을 부여하는 것입니다. 이러한 변수는 한 번만 할당됩니다. 이 의도는 [`const`](@ref) 키워드를 사용하여 컴파일러에 전달할 수 있습니다:

```jldoctest
julia> const e  = 2.71828182845904523536;

julia> const pi = 3.14159265358979323846;
```

여러 변수를 단일 `const` 문에서 선언할 수 있습니다:

```jldoctest
julia> const a, b = 1, 2
(1, 2)
```

`const` 선언은 전역 범위에서 전역 변수에만 사용해야 합니다. 전역 변수를 포함하는 코드를 최적화하는 것은 컴파일러에게 어려운 일입니다. 그 값(또는 심지어 그 타입)이 거의 언제든지 변경될 수 있기 때문입니다. 전역 변수가 변경되지 않을 경우, `const` 선언을 추가하면 이 성능 문제를 해결할 수 있습니다.

로컬 상수는 상당히 다릅니다. 컴파일러는 로컬 변수가 상수인지 자동으로 판단할 수 있으므로 로컬 상수 선언은 필요하지 않으며, 실제로 현재 지원되지 않습니다.

특별한 최상위 할당, 즉 `function` 및 `struct` 키워드에 의해 수행되는 할당은 기본적으로 상수입니다.

`const`는 변수 바인딩에만 영향을 미친다는 점에 유의하세요; 변수는 변경 가능한 객체(예: 배열)에 바인딩될 수 있으며, 해당 객체는 여전히 수정될 수 있습니다. 또한 상수로 선언된 변수에 값을 할당하려고 할 때 다음과 같은 시나리오가 발생할 수 있습니다:

  * 새로운 값이 상수의 타입과 다른 타입일 경우 오류가 발생합니다:

```jldoctest
julia> const x = 1.0
1.0

julia> x = 1
ERROR: invalid redefinition of constant x
```

  * 새로운 값이 상수와 동일한 유형인 경우 경고가 출력됩니다:

```jldoctest
julia> const y = 1.0
1.0

julia> y = 2.0
WARNING: redefinition of constant y. This may fail, cause incorrect answers, or produce other errors.
2.0
```

  * 변수 값의 변경이 없는 경우, 메시지가 제공되지 않습니다:

```jldoctest
julia> const z = 100
100

julia> z = 100
100
```

마지막 규칙은 변수 바인딩이 변경되더라도 불변 객체에 적용됩니다. 예를 들어:

```julia-repl
julia> const s1 = "1"
"1"

julia> s2 = "1"
"1"

julia> pointer.([s1, s2], 1)
2-element Array{Ptr{UInt8},1}:
 Ptr{UInt8} @0x00000000132c9638
 Ptr{UInt8} @0x0000000013dd3d18

julia> s1 = s2
"1"

julia> pointer.([s1, s2], 1)
2-element Array{Ptr{UInt8},1}:
 Ptr{UInt8} @0x0000000013dd3d18
 Ptr{UInt8} @0x0000000013dd3d18
```

그러나 변경 가능한 객체의 경우 경고가 예상대로 출력됩니다:

```jldoctest
julia> const a = [1]
1-element Vector{Int64}:
 1

julia> a = [1]
WARNING: redefinition of constant a. This may fail, cause incorrect answers, or produce other errors.
1-element Vector{Int64}:
 1
```

`const` 변수의 값을 변경하는 것은 때때로 가능하지만, 강력히 권장되지 않으며, 대화형 사용 중 편의를 위해서만 의도됩니다. 상수를 변경하면 다양한 문제나 예기치 않은 동작이 발생할 수 있습니다. 예를 들어, 메서드가 상수를 참조하고 상수가 변경되기 전에 이미 컴파일된 경우, 이전 값을 계속 사용할 수 있습니다:

```jldoctest
julia> const x = 1
1

julia> f() = x
f (generic function with 1 method)

julia> f()
1

julia> x = 2
WARNING: redefinition of constant x. This may fail, cause incorrect answers, or produce other errors.
2

julia> f()
1
```

## [Typed Globals](@id man-typed-globals)

!!! compat "Julia 1.8"
    Julia 1.8에서 타입이 지정된 전역 변수에 대한 지원이 추가되었습니다.


상수로 선언되는 것과 유사하게, 전역 바인딩도 항상 상수 유형으로 선언될 수 있습니다. 이는 실제 값을 할당하지 않고 `global x::T` 구문을 사용하여 수행할 수 있거나, 할당 시 `x::T = 123`과 같이 수행할 수 있습니다.

```jldoctest
julia> x::Float64 = 2.718
2.718

julia> f() = x
f (generic function with 1 method)

julia> Base.return_types(f)
1-element Vector{Any}:
 Float64
```

어떤 전역 변수에 대한 할당이든, Julia는 먼저 [`convert`](@ref)를 사용하여 적절한 유형으로 변환하려고 시도합니다:

```jldoctest
julia> global y::Int

julia> y = 1.0
1.0

julia> y
1

julia> y = 3.14
ERROR: InexactError: Int64(3.14)
Stacktrace:
[...]
```

유형은 구체적일 필요는 없지만, 추상 유형으로 주석을 달면 일반적으로 성능 이점이 거의 없습니다.

전역 변수가 할당되거나 그 유형이 설정된 후에는 바인딩 유형을 변경할 수 없습니다:

```jldoctest
julia> x = 1
1

julia> global x::Int
ERROR: cannot set type for global x. It already has a value or is already set to a different type.
Stacktrace:
[...]
```
