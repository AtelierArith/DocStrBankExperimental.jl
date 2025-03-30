# Control Flow

Julia는 다양한 제어 흐름 구조를 제공합니다:

  * [Compound Expressions](@ref man-compound-expressions): `시작` 및 `;`.
  * [Conditional Evaluation](@ref man-conditional-evaluation): `if`-`elseif`-`else` and `?:` (ternary operator).
  * [Short-Circuit Evaluation](@ref): 논리 연산자 `&&` (“그리고”) 및 `||` (“또는”), 그리고 연결된 비교.
  * [Repeated Evaluation: Loops](@ref man-loops): `동안` 및 `for`.
  * [Exception Handling](@ref): `시도`-`잡기`, [`error`](@ref) 및 [`throw`](@ref).
  * [Tasks (aka Coroutines)](@ref man-tasks): [`yieldto`](@ref).

첫 다섯 가지 제어 흐름 메커니즘은 고급 프로그래밍 언어에서 표준입니다. [`Task`](@ref)는 표준적이지 않습니다: 이들은 비지역 제어 흐름을 제공하여 일시 중단된 계산 간에 전환할 수 있게 합니다. 이는 강력한 구조입니다: 예외 처리와 협력적 다중 작업 모두 Julia에서 작업을 사용하여 구현됩니다. 일상적인 프로그래밍에서는 작업을 직접 사용할 필요가 없지만, 특정 문제는 작업을 사용하여 훨씬 더 쉽게 해결할 수 있습니다.

## [Compound Expressions](@id man-compound-expressions)

가끔 여러 하위 표현식을 순서대로 평가하고 마지막 하위 표현식의 값을 결과로 반환하는 단일 표현식이 편리할 수 있습니다. 이를 수행하는 두 가지 줄리아 구성 요소가 있습니다: `begin` 블록과 `;` 체인. 두 복합 표현식 구성 요소의 값은 마지막 하위 표현식의 값입니다. 다음은 `begin` 블록의 예입니다:

```jldoctest
julia> z = begin
           x = 1
           y = 2
           x + y
       end
3
```

이것들은 꽤 작고 간단한 표현이기 때문에 쉽게 한 줄에 배치할 수 있으며, 이때 `;` 체인 구문이 유용하게 사용됩니다:

```jldoctest
julia> z = (x = 1; y = 2; x + y)
3
```

이 구문은 [Functions](@ref man-functions)에서 도입된 간결한 단일 행 함수 정의 형식과 특히 유용합니다. 일반적이긴 하지만, `begin` 블록이 멀티라인일 필요는 없으며 `;` 체인이 단일 행일 필요도 없습니다:

```jldoctest
julia> begin x = 1; y = 2; x + y end
3

julia> (x = 1;
        y = 2;
        x + y)
3
```

## [Conditional Evaluation](@id man-conditional-evaluation)

조건부 평가는 부울 표현식의 값에 따라 코드의 일부가 평가되거나 평가되지 않도록 합니다. 다음은 `if`-`elseif`-`else` 조건부 구문의 구조입니다:

```julia
if x < y
    println("x is less than y")
elseif x > y
    println("x is greater than y")
else
    println("x is equal to y")
end
```

조건 표현식 `x < y`가 `true`인 경우, 해당 블록이 평가됩니다. 그렇지 않으면 조건 표현식 `x > y`가 평가되며, 만약 이것이 `true`라면 해당 블록이 평가됩니다. 두 표현식 모두 `true`가 아닌 경우, `else` 블록이 평가됩니다. 여기에서 작동하는 모습을 보여줍니다:

```jldoctest
julia> function test(x, y)
           if x < y
               println("x is less than y")
           elseif x > y
               println("x is greater than y")
           else
               println("x is equal to y")
           end
       end
test (generic function with 1 method)

julia> test(1, 2)
x is less than y

julia> test(2, 1)
x is greater than y

julia> test(1, 1)
x is equal to y
```

`elseif` 및 `else` 블록은 선택 사항이며, 원하는 만큼 많은 `elseif` 블록을 사용할 수 있습니다. `if`-`elseif`-`else` 구조의 조건 표현식은 첫 번째 표현식이 `true`로 평가될 때까지 평가되며, 그 이후에 관련된 블록이 평가되고 더 이상의 조건 표현식이나 블록은 평가되지 않습니다.

`if` 블록은 "누수" 현상이 있으며, 즉 지역 스코프를 도입하지 않습니다. 이는 `if` 절 안에서 정의된 새로운 변수가 `if` 블록 이후에도 사용할 수 있음을 의미합니다. 따라서 위의 `test` 함수를 다음과 같이 정의할 수 있습니다.

```jldoctest
julia> function test(x,y)
           if x < y
               relation = "less than"
           elseif x == y
               relation = "equal to"
           else
               relation = "greater than"
           end
           println("x is ", relation, " y.")
       end
test (generic function with 1 method)

julia> test(2, 1)
x is greater than y.
```

변수 `relation`은 `if` 블록 내에서 선언되지만, 외부에서 사용됩니다. 그러나 이 동작에 의존할 때는 모든 가능한 코드 경로가 변수에 대한 값을 정의하도록 해야 합니다. 위 함수에 대한 다음 변경은 런타임 오류를 초래합니다.

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> function test(x,y)
           if x < y
               relation = "less than"
           elseif x == y
               relation = "equal to"
           end
           println("x is ", relation, " y.")
       end
test (generic function with 1 method)

julia> test(1,2)
x is less than y.

julia> test(2,1)
ERROR: UndefVarError: `relation` not defined in local scope
Stacktrace:
 [1] test(::Int64, ::Int64) at ./none:7
```

`if` 블록은 또한 값을 반환하는데, 이는 많은 다른 언어에서 오는 사용자에게는 직관적이지 않을 수 있습니다. 이 값은 선택된 분기에서 마지막으로 실행된 문장의 반환 값입니다.

```jldoctest
julia> x = 3
3

julia> if x > 0
           "positive!"
       else
           "negative..."
       end
"positive!"
```

짧은 조건문(한 줄짜리)은 다음 섹션에서 설명된 대로 줄리아에서 단축 평가(Short-Circuit Evaluation)를 사용하여 자주 표현된다는 점에 유의하세요.

C와 MATLAB, Perl, Python, Ruby와는 달리 – Java 및 몇 가지 다른 엄격하고 타입이 있는 언어와 마찬가지로 – 조건 표현식의 값이 `true` 또는 `false`가 아닌 경우 오류가 발생합니다:

```jldoctest
julia> if 1
           println("true")
       end
ERROR: TypeError: non-boolean (Int64) used in boolean context
```

이 오류는 조건이 잘못된 유형임을 나타냅니다: [`Int64`](@ref)가 아니라 필요한 [`Bool`](@ref)입니다.

소위 "삼항 연산자"인 `?:`는 `if`-`elseif`-`else` 구문과 밀접하게 관련되어 있지만, 긴 코드 블록의 조건부 실행이 아닌 단일 표현식 값 간의 조건부 선택이 필요한 경우에 사용됩니다. 대부분의 언어에서 세 개의 피연산자를 사용하는 유일한 연산자이기 때문에 이러한 이름이 붙었습니다:

```julia
a ? b : c
```

표현식 `a`는 `?` 이전의 조건 표현식이며, 삼항 연산자는 조건 `a`가 `true`일 경우 `:` 이전의 표현식 `b`를 평가하고, `false`일 경우 `:` 이후의 표현식 `c`를 평가합니다. `?`와 `:` 주위의 공백은 필수입니다: `a?b:c`와 같은 표현식은 유효한 삼항 표현식이 아닙니다(하지만 `?`와 `:` 뒤에 줄 바꿈은 허용됩니다).

이 행동을 이해하는 가장 쉬운 방법은 예제를 보는 것입니다. 이전 예제에서 `println` 호출은 세 가지 분기 모두에 의해 공유됩니다: 실제로 선택할 수 있는 것은 어떤 리터럴 문자열을 출력할 것인지입니다. 이는 삼항 연산자를 사용하여 더 간결하게 작성할 수 있습니다. 명확성을 위해, 먼저 양방향 버전을 시도해 봅시다:

```jldoctest
julia> x = 1; y = 2;

julia> println(x < y ? "less than" : "not less than")
less than

julia> x = 1; y = 0;

julia> println(x < y ? "less than" : "not less than")
not less than
```

`x < y`가 참이면 전체 삼항 연산자 표현식은 문자열 `"less than"`으로 평가되고, 그렇지 않으면 문자열 `"not less than"`으로 평가됩니다. 원래의 삼중 예제는 여러 번의 삼항 연산자를 연결해야 합니다:

```jldoctest
julia> test(x, y) = println(x < y ? "x is less than y"    :
                            x > y ? "x is greater than y" : "x is equal to y")
test (generic function with 1 method)

julia> test(1, 2)
x is less than y

julia> test(2, 1)
x is greater than y

julia> test(1, 1)
x is equal to y
```

체이닝을 용이하게 하기 위해, 연산자는 오른쪽에서 왼쪽으로 결합합니다.

`if`-`elseif`-`else`와 마찬가지로, `:` 앞과 뒤의 표현식은 조건 표현식이 각각 `true` 또는 `false`로 평가될 때만 평가된다는 점이 중요합니다:

```jldoctest
julia> v(x) = (println(x); x)
v (generic function with 1 method)

julia> 1 < 2 ? v("yes") : v("no")
yes
"yes"

julia> 1 > 2 ? v("yes") : v("no")
no
"no"
```

## Short-Circuit Evaluation

`&&` 및 `||` 연산자는 Julia에서 각각 논리 "그리고" 및 "또는" 연산에 해당하며, 일반적으로 이러한 목적으로 사용됩니다. 그러나 이들은 *단락* 평가의 추가 속성을 가지고 있습니다: 아래에 설명된 대로 두 번째 인수를 반드시 평가하지는 않습니다. (단락 동작 없이 논리 "그리고" 및 "또는"으로 사용할 수 있는 비트 단위 `&` 및 `|` 연산자도 있지만, `&` 및 `|`는 평가 순서에서 `&&` 및 `||`보다 우선 순위가 더 높다는 점에 유의해야 합니다.)

단락 평가(short-circuit evaluation)는 조건부 평가와 매우 유사합니다. 이 동작은 `&&` 및 `||` 불리언 연산자를 가진 대부분의 명령형 프로그래밍 언어에서 발견됩니다: 이러한 연산자로 연결된 일련의 불리언 표현식에서 전체 체인의 최종 불리언 값을 결정하는 데 필요한 최소한의 표현식만 평가됩니다. 일부 언어(예: Python)는 이를 `and` (`&&`) 및 `or` (`||`)라고 부릅니다. 명시적으로 말하자면, 이는 다음을 의미합니다:

  * 표현식 `a && b`에서, 하위 표현식 `b`는 `a`가 `true`로 평가될 때만 평가됩니다.
  * 표현식 `a || b`에서, 부분 표현식 `b`는 `a`가 `false`로 평가될 때만 평가됩니다.

이유는 `a && b`가 `a`가 `false`일 경우 `b`의 값에 관계없이 `false`여야 하고, 마찬가지로 `a || b`의 값은 `a`가 `true`일 경우 `b`의 값에 관계없이 `true`여야 한다는 것입니다. `&&`와 `||`는 모두 오른쪽으로 결합되지만, `&&`는 `||`보다 우선 순위가 높습니다. 이 동작을 실험해보는 것은 쉽습니다:

```jldoctest tandf
julia> t(x) = (println(x); true)
t (generic function with 1 method)

julia> f(x) = (println(x); false)
f (generic function with 1 method)

julia> t(1) && t(2)
1
2
true

julia> t(1) && f(2)
1
2
false

julia> f(1) && t(2)
1
false

julia> f(1) && f(2)
1
false

julia> t(1) || t(2)
1
true

julia> t(1) || f(2)
1
true

julia> f(1) || t(2)
1
2
true

julia> f(1) || f(2)
1
2
false
```

여러 조합의 `&&` 및 `||` 연산자의 결합성과 우선순위에 대해 같은 방식으로 쉽게 실험할 수 있습니다.

이 행동은 줄리아에서 매우 짧은 `if` 문에 대한 대안으로 자주 사용됩니다. `if <cond> <statement> end` 대신에 `<cond> && <statement>`라고 쓸 수 있습니다 (이는 <cond> *그리고 나서* <statement>로 읽을 수 있습니다). 마찬가지로, `if ! <cond> <statement> end` 대신에 `<cond> || <statement>`라고 쓸 수 있습니다 (이는 <cond> *또는* <statement>로 읽을 수 있습니다).

예를 들어, 재귀 팩토리얼 루틴은 다음과 같이 정의될 수 있습니다:

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> function fact(n::Int)
           n >= 0 || error("n must be non-negative")
           n == 0 && return 1
           n * fact(n-1)
       end
fact (generic function with 1 method)

julia> fact(5)
120

julia> fact(0)
1

julia> fact(-1)
ERROR: n must be non-negative
Stacktrace:
 [1] error at ./error.jl:33 [inlined]
 [2] fact(::Int64) at ./none:2
 [3] top-level scope
```

부울 연산 *단축 회피 없이*는 [Mathematical Operations and Elementary Functions](@ref)에서 도입된 비트 단위 부울 연산자 `&`와 `|`를 사용하여 수행할 수 있습니다. 이들은 일반 함수로, 중위 연산자 구문을 지원하지만 항상 인수를 평가합니다:

```jldoctest tandf
julia> f(1) & t(2)
1
2
false

julia> t(1) | t(2)
1
2
true
```

`if`, `elseif` 또는 삼항 연산자에서 사용되는 조건 표현식과 마찬가지로, `&&` 또는 `||`의 피연산자는 불리언 값(`true` 또는 `false`)이어야 합니다. 조건 체인의 마지막 항목을 제외한 곳에서 비불리언 값을 사용하는 것은 오류입니다:

```jldoctest
julia> 1 && true
ERROR: TypeError: non-boolean (Int64) used in boolean context
```

반면, 조건 체인의 끝에는 어떤 유형의 표현식도 사용할 수 있습니다. 이는 앞선 조건에 따라 평가되고 반환됩니다:

```jldoctest
julia> true && (x = (1, 2, 3))
(1, 2, 3)

julia> false && (x = (1, 2, 3))
false
```

## [Repeated Evaluation: Loops](@id man-loops)

반복적으로 표현식을 평가하기 위한 두 가지 구조가 있습니다: `while` 루프와 `for` 루프. 다음은 `while` 루프의 예입니다:

```jldoctest
julia> i = 1;

julia> while i <= 3
           println(i)
           global i += 1
       end
1
2
3
```

`while` 루프는 조건 표현식(`i <= 3`인 경우)을 평가하며, 조건이 `true`인 동안에는 `while` 루프의 본문도 계속 평가합니다. `while` 루프에 처음 도달했을 때 조건 표현식이 `false`이면 본문은 절대 평가되지 않습니다.

`for` 루프는 일반적인 반복 평가 관용구를 작성하기 쉽게 만듭니다. 위의 `while` 루프처럼 위아래로 세는 것이 매우 일반적이기 때문에, `for` 루프를 사용하여 더 간결하게 표현할 수 있습니다:

```jldoctest
julia> for i = 1:3
           println(i)
       end
1
2
3
```

Here the `1:3` is a [`range`](@ref) object, representing the sequence of numbers 1, 2, 3. The `for` loop iterates through these values, assigning each one in turn to the variable `i`. In general, the `for` construct can loop over any "iterable" object (or "container"), from a  range like `1:3` or `1:3:13` (a [`StepRange`](@ref) indicating every 3rd integer 1, 4, 7, …, 13) to more generic containers like arrays, including [iterators defined by user code](@ref man-interface-iteration) or external packages. For containers other than ranges, the alternative (but fully equivalent) keyword `in` or `∈` is typically used instead of `=`, since it makes the code read more clearly:

```jldoctest
julia> for i in [1,4,0]
           println(i)
       end
1
4
0

julia> for s ∈ ["foo","bar","baz"]
           println(s)
       end
foo
bar
baz
```

매뉴얼의 후속 섹션에서는 다양한 유형의 반복 가능한 컨테이너가 소개되고 논의될 것입니다 (예: [Multi-dimensional Arrays](@ref man-multi-dim-arrays)).

이전 `while` 루프 형식과 `for` 루프 형식 간의 중요한 구분 중 하나는 변수가 가시적인 범위입니다. `for` 루프는 항상 본문에서 새로운 반복 변수를 도입하며, 이는 동일한 이름의 변수가 포함된 범위에 존재하더라도 마찬가지입니다. 이는 한편으로 `i`가 루프 전에 선언될 필요가 없음을 의미합니다. 다른 한편으로는 루프 외부에서 가시적이지 않으며, 동일한 이름의 외부 변수에도 영향을 미치지 않습니다. 이를 테스트하려면 새로운 대화형 세션 인스턴스나 다른 변수 이름이 필요합니다:

```jldoctest
julia> for j = 1:3
           println(j)
       end
1
2
3

julia> j
ERROR: UndefVarError: `j` not defined in `Main`
```

```jldoctest
julia> j = 0;

julia> for j = 1:3
           println(j)
       end
1
2
3

julia> j
0
```

`for outer`를 사용하여 후자의 동작을 수정하고 기존의 지역 변수를 재사용하십시오.

[Scope of Variables](@ref scope-of-variables)의 변수 범위에 대한 자세한 설명과 [`outer`](@ref)가 Julia에서 어떻게 작동하는지 확인하세요.

때때로 `while`의 반복을 테스트 조건이 거짓으로 바뀌기 전에 종료하거나 `for` 루프에서 반복 가능한 객체의 끝에 도달하기 전에 반복을 중단하는 것이 편리할 수 있습니다. 이는 `break` 키워드를 사용하여 수행할 수 있습니다:

```jldoctest
julia> i = 1;

julia> while true
           println(i)
           if i >= 3
               break
           end
           global i += 1
       end
1
2
3

julia> for j = 1:1000
           println(j)
           if j >= 3
               break
           end
       end
1
2
3
```

`break` 키워드가 없으면 위의 `while` 루프는 스스로 종료되지 않으며, `for` 루프는 1000까지 반복됩니다. 이 두 루프는 모두 `break`를 사용하여 조기에 종료됩니다.

다른 상황에서는 반복을 중단하고 즉시 다음 반복으로 이동할 수 있는 것이 유용합니다. `continue` 키워드는 이를 수행합니다:

```jldoctest
julia> for i = 1:10
           if i % 3 != 0
               continue
           end
           println(i)
       end
3
6
9
```

이것은 다소 인위적인 예입니다. 왜냐하면 조건을 부정하고 `if` 블록 안에 `println` 호출을 배치함으로써 같은 동작을 더 명확하게 생성할 수 있기 때문입니다. 실제 사용에서는 `continue` 이후에 평가해야 할 코드가 더 많고, 종종 `continue`를 호출하는 여러 지점이 있습니다.

여러 개의 중첩된 `for` 루프는 단일 외부 루프로 결합될 수 있으며, 이는 그 반복 가능한 객체의 데카르트 곱을 형성합니다:

```jldoctest
julia> for i = 1:2, j = 3:4
           println((i, j))
       end
(1, 3)
(1, 4)
(2, 3)
(2, 4)
```

이 구문을 사용하면 반복 가능한 객체가 여전히 외부 루프 변수를 참조할 수 있습니다. 예를 들어, `for i = 1:n, j = 1:i`는 유효합니다. 그러나 이러한 루프 내부에 있는 `break` 문은 내부 루프만이 아니라 전체 루프를 종료합니다. 두 변수(`i`와 `j`)는 내부 루프가 실행될 때마다 현재 반복 값으로 설정됩니다. 따라서 `i`에 대한 할당은 이후 반복에서 볼 수 없습니다:

```jldoctest
julia> for i = 1:2, j = 3:4
           println((i, j))
           i = 0
       end
(1, 3)
(1, 4)
(2, 3)
(2, 4)
```

이 예제가 각 변수에 대해 `for` 키워드를 사용하도록 다시 작성된다면, 출력은 달라질 것입니다: 두 번째와 네 번째 값은 `0`을 포함하게 됩니다.

여러 컨테이너를 동시에 반복할 수 있습니다 `for` 루프를 사용하여 [`zip`](@ref):

```jldoctest
julia> for (j, k) in zip([1 2 3], [4 5 6 7])
           println((j,k))
       end
(1, 4)
(2, 5)
(3, 6)
```

[`zip`](@ref)를 사용하면 전달된 컨테이너에 대한 서브이터레이터를 포함하는 튜플을 생성하는 이터레이터가 생성됩니다. `zip` 이터레이터는 모든 서브이터레이터를 순서대로 반복하며, `for` 루프의 $i$번째 반복에서 각 서브이터레이터의 $i$번째 요소를 선택합니다. 서브이터레이터 중 하나가 소진되면 `for` 루프는 중지됩니다.

## Exception Handling

예기치 않은 조건이 발생할 때, 함수는 호출자에게 합리적인 값을 반환할 수 없을 수 있습니다. 이러한 경우, 예외적인 조건이 진단 오류 메시지를 출력하면서 프로그램을 종료하는 것이 가장 좋거나, 프로그래머가 이러한 예외적인 상황을 처리하기 위한 코드를 제공한 경우에는 해당 코드가 적절한 조치를 취하도록 허용하는 것이 좋습니다.

### Built-in `Exception`s

`Exception`은 예상치 못한 조건이 발생했을 때 발생합니다. 아래에 나열된 내장 `Exception`은 모두 정상적인 제어 흐름을 중단시킵니다.

| `Exception`                   |
|:----------------------------- |
| [`ArgumentError`](@ref)       |
| [`BoundsError`](@ref)         |
| [`CompositeException`](@ref)  |
| [`DimensionMismatch`](@ref)   |
| [`DivideError`](@ref)         |
| [`DomainError`](@ref)         |
| [`EOFError`](@ref)            |
| [`ErrorException`](@ref)      |
| [`InexactError`](@ref)        |
| [`InitError`](@ref)           |
| [`InterruptException`](@ref)  |
| `InvalidStateException`       |
| [`KeyError`](@ref)            |
| [`LoadError`](@ref)           |
| [`OutOfMemoryError`](@ref)    |
| [`ReadOnlyMemoryError`](@ref) |
| [`RemoteException`](@ref)     |
| [`MethodError`](@ref)         |
| [`OverflowError`](@ref)       |
| [`Meta.ParseError`](@ref)     |
| [`SystemError`](@ref)         |
| [`TypeError`](@ref)           |
| [`UndefRefError`](@ref)       |
| [`UndefVarError`](@ref)       |
| [`StringIndexError`](@ref)    |

예를 들어, [`sqrt`](@ref) 함수는 음의 실수 값에 적용될 경우 [`DomainError`](@ref)를 발생시킵니다:

```jldoctest
julia> sqrt(-1)
ERROR: DomainError with -1.0:
sqrt was called with a negative real argument but will only return a complex result if called with a complex argument. Try sqrt(Complex(x)).
Stacktrace:
[...]
```

다음과 같은 방법으로 자신만의 예외를 정의할 수 있습니다:

```jldoctest
julia> struct MyCustomException <: Exception end
```

### The [`throw`](@ref) function

예외는 [`throw`](@ref)로 명시적으로 생성할 수 있습니다. 예를 들어, 음이 아닌 숫자에 대해서만 정의된 함수는 인수가 음수일 경우 [`DomainError`](@ref)로 작성될 수 있습니다:

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> f(x) = x>=0 ? exp(-x) : throw(DomainError(x, "argument must be non-negative"))
f (generic function with 1 method)

julia> f(1)
0.36787944117144233

julia> f(-1)
ERROR: DomainError with -1:
argument must be non-negative
Stacktrace:
 [1] f(::Int64) at ./none:1
```

[`DomainError`](@ref)는 괄호 없이 예외가 아니라 예외의 일종임을 유의하십시오. `Exception` 객체를 얻기 위해 호출해야 합니다:

```jldoctest
julia> typeof(DomainError(nothing)) <: Exception
true

julia> typeof(DomainError) <: Exception
false
```

또한, 일부 예외 유형은 오류 보고에 사용되는 하나 이상의 인수를 받습니다:

```jldoctest
julia> throw(UndefVarError(:x))
ERROR: UndefVarError: `x` not defined
```

이 메커니즘은 [`UndefVarError`](@ref)가 작성된 방식에 따라 사용자 정의 예외 유형을 통해 쉽게 구현할 수 있습니다:

```jldoctest
julia> struct MyUndefVarError <: Exception
           var::Symbol
       end

julia> Base.showerror(io::IO, e::MyUndefVarError) = print(io, e.var, " not defined")
```

!!! note
    오류 메시지를 작성할 때는 첫 번째 단어를 소문자로 작성하는 것이 좋습니다. 예를 들어,

    `size(A) == size(B) || throw(DimensionMismatch("A의 크기가 B의 크기와 같지 않습니다."))`

    선호됨

    `size(A) == size(B) || throw(DimensionMismatch("A의 크기가 B의 크기와 같지 않습니다."))`.

    그러나 때때로 함수에 대한 인수가 대문자인 경우와 같이 대문자 첫 글자를 유지하는 것이 의미가 있습니다:

    `size(A,1) == size(B,2) || throw(DimensionMismatch("A의 첫 번째 차원..."))`.


### Errors

[`error`](@ref) 함수는 정상적인 제어 흐름을 중단하는 [`ErrorException`](@ref)을 생성하는 데 사용됩니다.

부정적인 수의 제곱근을 취할 경우 즉시 실행을 중단하고자 한다면, 인수가 부정적일 경우 오류를 발생시키는 [`sqrt`](@ref) 함수의 모호한 버전을 정의할 수 있습니다:

```jldoctest fussy_sqrt; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> fussy_sqrt(x) = x >= 0 ? sqrt(x) : error("negative x not allowed")
fussy_sqrt (generic function with 1 method)

julia> fussy_sqrt(2)
1.4142135623730951

julia> fussy_sqrt(-1)
ERROR: negative x not allowed
Stacktrace:
 [1] error at ./error.jl:33 [inlined]
 [2] fussy_sqrt(::Int64) at ./none:1
 [3] top-level scope
```

`fussy_sqrt`가 다른 함수에서 음수 값을 호출할 경우, 호출하는 함수의 실행을 계속하려고 시도하는 대신 즉시 반환하며, 대화형 세션에 오류 메시지를 표시합니다:

```jldoctest fussy_sqrt; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> function verbose_fussy_sqrt(x)
           println("before fussy_sqrt")
           r = fussy_sqrt(x)
           println("after fussy_sqrt")
           return r
       end
verbose_fussy_sqrt (generic function with 1 method)

julia> verbose_fussy_sqrt(2)
before fussy_sqrt
after fussy_sqrt
1.4142135623730951

julia> verbose_fussy_sqrt(-1)
before fussy_sqrt
ERROR: negative x not allowed
Stacktrace:
 [1] error at ./error.jl:33 [inlined]
 [2] fussy_sqrt at ./none:1 [inlined]
 [3] verbose_fussy_sqrt(::Int64) at ./none:3
 [4] top-level scope
```

### The `try/catch` statement

`try/catch` 문은 `Exception`을 테스트하고 일반적으로 애플리케이션을 중단시킬 수 있는 상황을 우아하게 처리할 수 있게 해줍니다. 예를 들어, 아래 코드에서 제곱근 함수는 일반적으로 예외를 발생시킵니다. 그 주위에 `try/catch` 블록을 배치함으로써 우리는 여기서 이를 완화할 수 있습니다. 이 예외를 처리하는 방법은 로깅을 하거나 자리 표시자 값을 반환하거나 아래의 경우처럼 단순히 문장을 출력하는 등 선택할 수 있습니다. 예기치 않은 상황을 처리하는 방법을 결정할 때 고려해야 할 한 가지는 `try/catch` 블록을 사용하는 것이 그러한 상황을 처리하기 위해 조건 분기를 사용하는 것보다 훨씬 느리다는 것입니다. 아래에는 `try/catch` 블록을 사용하여 예외를 처리하는 더 많은 예가 있습니다:

```jldoctest
julia> try
           sqrt("ten")
       catch e
           println("You should have entered a numeric value")
       end
You should have entered a numeric value
```

`try/catch` 문은 `Exception`을 변수에 저장할 수 있도록 합니다. 다음의 인위적인 예제는 `x`가 인덱스 가능할 경우 `x`의 두 번째 요소의 제곱근을 계산하고, 그렇지 않으면 `x`가 실수라고 가정하고 그 제곱근을 반환합니다:

```jldoctest
julia> sqrt_second(x) = try
           sqrt(x[2])
       catch y
           if isa(y, DomainError)
               sqrt(complex(x[2], 0))
           elseif isa(y, BoundsError)
               sqrt(x)
           end
       end
sqrt_second (generic function with 1 method)

julia> sqrt_second([1 4])
2.0

julia> sqrt_second([1 -4])
0.0 + 2.0im

julia> sqrt_second(9)
3.0

julia> sqrt_second(-9)
ERROR: DomainError with -9.0:
sqrt was called with a negative real argument but will only return a complex result if called with a complex argument. Try sqrt(Complex(x)).
Stacktrace:
[...]
```

`catch` 다음의 기호는 항상 예외의 이름으로 해석되므로, 한 줄에 `try/catch` 표현식을 작성할 때 주의가 필요합니다. 다음 코드는 오류가 발생할 경우 `x`의 값을 반환하지 않습니다:

```julia
try bad() catch x end
```

대신 `catch` 뒤에 세미콜론을 사용하거나 줄 바꿈을 삽입하세요:

```julia
try bad() catch; x end

try bad()
catch
    x
end
```

`try/catch` 구조의 힘은 깊게 중첩된 계산을 호출 함수 스택의 훨씬 높은 수준으로 즉시 풀 수 있는 능력에 있습니다. 오류가 발생하지 않은 상황에서도 스택을 풀고 더 높은 수준으로 값을 전달하는 능력이 바람직한 경우가 있습니다. Julia는 더 고급 오류 처리를 위해 [`rethrow`](@ref), [`backtrace`](@ref), [`catch_backtrace`](@ref) 및 [`current_exceptions`](@ref) 함수를 제공합니다.

### `else` Clauses

!!! compat "Julia 1.8"
    이 기능은 최소한 Julia 1.8이 필요합니다.


경우에 따라, 오류 케이스를 적절하게 처리하는 것뿐만 아니라 `try` 블록이 성공할 경우에만 코드를 실행하고 싶을 수도 있습니다. 이를 위해 `catch` 블록 뒤에 `else` 절을 지정할 수 있으며, 이는 이전에 오류가 발생하지 않았을 때 실행됩니다. 이 코드를 `try` 블록에 포함시키는 것보다 이점은 추가적인 오류가 `catch` 절에 의해 조용히 잡히지 않는다는 것입니다.

```julia
local x
try
    x = read("file", String)
catch
    # handle read errors
else
    # do something with x
end
```

!!! note
    `try`, `catch`, `else`, `finally` 절은 각각 자신의 범위 블록을 도입하므로, 변수가 `try` 블록에서만 정의된 경우 `else` 또는 `finally` 절에서 접근할 수 없습니다:

    ```jldoctest
    julia> try
               foo = 1
           catch
           else
               foo
           end
    ERROR: UndefVarError: `foo` not defined in `Main`
    Suggestion: check for spelling errors or missing imports.
    ```

    [`local` keyword](@ref local-scope)를 `try` 블록 외부에서 사용하여 변수를 외부 스코프 내 어디에서나 접근할 수 있도록 하세요.


### `finally` Clauses

상태 변경을 수행하거나 파일과 같은 리소스를 사용하는 코드에서는 일반적으로 코드가 완료될 때 수행해야 하는 정리 작업(예: 파일 닫기)이 필요합니다. 예외는 코드 블록이 정상적으로 끝나기 전에 종료될 수 있기 때문에 이 작업을 복잡하게 만들 수 있습니다. `finally` 키워드는 주어진 코드 블록이 어떻게 종료되든 관계없이 해당 블록이 종료될 때 일부 코드를 실행할 수 있는 방법을 제공합니다.

예를 들어, 열린 파일이 닫히도록 보장하는 방법은 다음과 같습니다:

```julia
f = open("file")
try
    # operate on file f
finally
    close(f)
end
```

`try` 블록을 벗어날 때(예: `return`으로 인해, 또는 정상적으로 종료될 때) `close(f)`가 실행됩니다. `try` 블록이 예외로 인해 종료되면, 예외는 계속 전파됩니다. `catch` 블록은 `try` 및 `finally`와 결합될 수 있습니다. 이 경우 `finally` 블록은 `catch`가 오류를 처리한 후에 실행됩니다.

## [Tasks (aka Coroutines)](@id man-tasks)

작업은 계산을 유연하게 일시 중지하고 재개할 수 있는 제어 흐름 기능입니다. 우리는 여기서 완전성을 위해 언급합니다; 전체 논의는 [Asynchronous Programming](@ref man-asynchronous)를 참조하십시오.
