# Mathematical Operations and Elementary Functions

Julia는 모든 숫자 원시 유형에 걸쳐 기본 산술 및 비트 연산자의 완전한 컬렉션을 제공하며, 포터블하고 효율적인 구현을 통해 포괄적인 표준 수학 함수 컬렉션을 제공합니다.

## Arithmetic Operators

다음 [arithmetic operators](https://en.wikipedia.org/wiki/Arithmetic#Arithmetic_operations)는 모든 원시 숫자 유형에서 지원됩니다:

| Expression | Name           | Description                            |
|:---------- |:-------------- |:-------------------------------------- |
| `+x`       | unary plus     | the identity operation                 |
| `-x`       | unary minus    | maps values to their additive inverses |
| `x + y`    | binary plus    | performs addition                      |
| `x - y`    | binary minus   | performs subtraction                   |
| `x * y`    | times          | performs multiplication                |
| `x / y`    | divide         | performs division                      |
| `x ÷ y`    | integer divide | x / y, truncated to an integer         |
| `x \ y`    | inverse divide | equivalent to `y / x`                  |
| `x ^ y`    | power          | raises `x` to the `y`th power          |
| `x % y`    | remainder      | equivalent to `rem(x, y)`              |

숫자 리터럴이 식별자나 괄호 바로 앞에 위치할 경우, 예를 들어 `2x` 또는 `2(x + y)`와 같이, 이는 곱셈으로 처리되지만 다른 이항 연산보다 우선 순위가 높습니다. 자세한 내용은 [Numeric Literal Coefficients](@ref man-numeric-literal-coefficients)를 참조하십시오.

줄리아의 승격 시스템은 인수 유형의 혼합에 대한 산술 연산이 "자연스럽고 자동으로" 작동하도록 만듭니다. 승격 시스템에 대한 자세한 내용은 [Conversion and Promotion](@ref conversion-and-promotion)을 참조하세요.

÷ 기호는 REPL 또는 Julia IDE에서 `\div<tab>`를 입력하여 편리하게 입력할 수 있습니다. 자세한 내용은 [manual section on Unicode input](@ref Unicode-Input)를 참조하세요.

다음은 산술 연산자를 사용하는 간단한 예입니다:

```jldoctest
julia> 1 + 2 + 3
6

julia> 1 - 2
-1

julia> 3*2/12
0.5
```

(관례상, 우리는 인접한 다른 연산자보다 먼저 적용되는 연산자에 대해 더 촘촘하게 간격을 두는 경향이 있습니다. 예를 들어, 우리는 일반적으로 `-x + 2`라고 작성하여 첫 번째 `x`가 부정되고, 그 결과에 `2`가 더해진다는 것을 반영합니다.)

곱셈에 사용될 때, `false`는 *강한 제로*로 작용합니다:

```jldoctest
julia> NaN * false
0.0

julia> false * Inf
0.0
```

이것은 0으로 알려진 양에서 `NaN` 값의 전파를 방지하는 데 유용합니다. 동기를 위해 [Knuth (1992)](https://arxiv.org/abs/math/9205211)를 참조하세요.

## Boolean Operators

다음 [Boolean operators](https://en.wikipedia.org/wiki/Boolean_algebra#Operations)는 [`Bool`](@ref) 유형에서 지원됩니다:

| Expression | Name                                                    |
|:---------- |:------------------------------------------------------- |
| `!x`       | negation                                                |
| `x && y`   | [short-circuiting and](@ref man-conditional-evaluation) |
| `x \|\| y` | [short-circuiting or](@ref man-conditional-evaluation)  |

부정은 `true`를 `false`로, 그리고 그 반대도 마찬가지로 변경합니다. 단축 평가 연산자는 링크된 페이지에서 설명되어 있습니다.

`Bool`은 정수형 타입이며, 모든 일반적인 승격 규칙과 수치 연산자도 이에 대해 정의되어 있습니다.

## Bitwise Operators

다음 [bitwise operators](https://en.wikipedia.org/wiki/Bitwise_operation#Bitwise_operators)는 모든 원시 정수 유형에서 지원됩니다:

| Expression | Name                                                                     |
|:---------- |:------------------------------------------------------------------------ |
| `~x`       | bitwise not                                                              |
| `x & y`    | bitwise and                                                              |
| `x \| y`   | bitwise or                                                               |
| `x ⊻ y`    | bitwise xor (exclusive or)                                               |
| `x ⊼ y`    | bitwise nand (not and)                                                   |
| `x ⊽ y`    | bitwise nor (not or)                                                     |
| `x >>> y`  | [logical shift](https://en.wikipedia.org/wiki/Logical_shift) right       |
| `x >> y`   | [arithmetic shift](https://en.wikipedia.org/wiki/Arithmetic_shift) right |
| `x << y`   | logical/arithmetic shift left                                            |

여기 비트 연산자를 사용한 몇 가지 예가 있습니다:

```jldoctest
julia> ~123
-124

julia> 123 & 234
106

julia> 123 | 234
251

julia> 123 ⊻ 234
145

julia> xor(123, 234)
145

julia> nand(123, 123)
-124

julia> 123 ⊼ 123
-124

julia> nor(123, 124)
-128

julia> 123 ⊽ 124
-128

julia> ~UInt32(123)
0xffffff84

julia> ~UInt8(123)
0x84
```

## Updating operators

모든 이진 산술 및 비트 연산자는 결과를 왼쪽 피연산자에 다시 할당하는 업데이트 버전도 있습니다. 이진 연산자의 업데이트 버전은 연산자 바로 뒤에 `=`를 배치하여 형성됩니다. 예를 들어, `x += 3`이라고 쓰는 것은 `x = x + 3`이라고 쓰는 것과 같습니다:

```jldoctest
julia> x = 1
1

julia> x += 3
4

julia> x
4
```

모든 이진 산술 및 비트 연산자의 업데이트된 버전은 다음과 같습니다:

```
+=  -=  *=  /=  \=  ÷=  %=  ^=  &=  |=  ⊻=  >>>=  >>=  <<=
```

!!! note
    업데이트 연산자는 왼쪽에 있는 변수의 바인딩을 다시 설정합니다. 그 결과, 변수의 타입이 변경될 수 있습니다.

    ```jldoctest
    julia> x = 0x01; typeof(x)
    UInt8

    julia> x *= 2 # Same as x = x * 2
    2

    julia> typeof(x)
    Int64
    ```


## [Vectorized "dot" operators](@id man-dot-operators)

모든 이진 연산자 `^`에 대해, 배열에서 요소별로 `^`를 수행하도록 자동으로 정의된 해당 "점" 연산 `.^`가 있습니다. 예를 들어, `[1, 2, 3] ^ 3`은 정의되지 않는데, 이는 (비정사각형) 배열을 "세제곱"하는 것에 대한 표준 수학적 의미가 없기 때문입니다. 그러나 `[1, 2, 3] .^ 3`은 요소별(또는 "벡터화된") 결과 `[1^3, 2^3, 3^3]`를 계산하는 것으로 정의됩니다. 마찬가지로 `!` 또는 `√`와 같은 단항 연산자에 대해서도 요소별로 연산자를 적용하는 해당 `.√`가 있습니다.

```jldoctest
julia> [1, 2, 3] .^ 3
3-element Vector{Int64}:
  1
  8
 27
```

더 구체적으로, `a .^ b`는 ["dot" call](@ref man-vectorized) `(^).(a,b)`로 파싱되며, 이는 [broadcast](@ref Broadcasting) 연산을 수행합니다: 이는 배열과 스칼라, 같은 크기의 배열(요소별로 연산 수행), 심지어 서로 다른 형태의 배열(예: 행 벡터와 열 벡터를 결합하여 행렬을 생성)도 결합할 수 있습니다. 게다가, 모든 벡터화된 "점 호출"처럼, 이러한 "점 연산자"는 *융합*됩니다. 예를 들어, 배열 `A`에 대해 `2 .* A.^2 .+ sin.(A)` (또는 동등하게 `@. 2A^2 + sin(A)`, [`@.`](@ref @__dot__) 매크로를 사용하여) 를 계산하면, `A`에 대해 `2a^2 + sin(a)`를 각 요소 `a`에 대해 계산하는 *단일* 루프를 수행합니다. 특히, `f.(g.(x))`와 같은 중첩된 점 호출은 융합되며, `x .+ 3 .* x.^2`와 같은 "인접한" 이진 연산자는 중첩된 점 호출 `(+).(x, (*).(3, (^).(x, 2)))`와 동등합니다.

Furthermore, "dotted" updating operators like `a .+= b` (or `@. a += b`) are parsed as `a .= a .+ b`, where `.=` is a fused *in-place* assignment operation (see the [dot syntax documentation](@ref man-vectorized)).

점(dot) 구문은 사용자 정의 연산자에도 적용됩니다. 예를 들어, `⊗(A, B) = kron(A, B)`를 정의하여 크로네커 곱에 대한 편리한 중위 구문 `A ⊗ B`를 제공하면([`kron`](@ref)), `[A, B] .⊗ [C, D]`는 추가 코딩 없이 `[A⊗C, B⊗D]`를 계산합니다.

점 연산자를 숫자 리터럴과 결합하는 것은 모호할 수 있습니다. 예를 들어, `1.+x`가 `1. + x`를 의미하는지 아니면 `1 .+ x`를 의미하는지 명확하지 않습니다. 따라서 이 구문은 허용되지 않으며, 이러한 경우 연산자 주위에 공백을 사용해야 합니다.

## Numeric Comparisons

모든 기본 숫자 유형에 대해 표준 비교 연산이 정의되어 있습니다:

| Operator                     | Name                     |
|:---------------------------- |:------------------------ |
| [`==`](@ref)                 | equality                 |
| [`!=`](@ref), [`≠`](@ref !=) | inequality               |
| [`<`](@ref)                  | less than                |
| [`<=`](@ref), [`≤`](@ref <=) | less than or equal to    |
| [`>`](@ref)                  | greater than             |
| [`>=`](@ref), [`≥`](@ref >=) | greater than or equal to |

여기 몇 가지 간단한 예시가 있습니다:

```jldoctest
julia> 1 == 1
true

julia> 1 == 2
false

julia> 1 != 2
true

julia> 1 == 1.0
true

julia> 1 < 2
true

julia> 1.0 > 3
false

julia> 1 >= 1.0
true

julia> -1 <= 1
true

julia> -1 <= -1
true

julia> -1 <= -2
false

julia> 3 < -0.5
false
```

정수는 비트 비교를 통해 표준 방식으로 비교됩니다. 부동 소수점 숫자는 [IEEE 754 standard](https://en.wikipedia.org/wiki/IEEE_754-2008)에 따라 비교됩니다:

  * 유한 수는 일반적인 방식으로 정렬됩니다.
  * 양의 제로는 음의 제로와 같지만 더 크지는 않습니다.
  * `Inf`는 자신과 같고 `NaN`을 제외한 모든 것보다 큽니다.
  * `-Inf`는 자신과 같고 `NaN`을 제외한 모든 것보다 작습니다.
  * `NaN`은 자신을 포함하여 어떤 것과도 같지 않으며, 작지도 크지도 않습니다.

마지막 포인트는 잠재적으로 놀라울 수 있으므로 주목할 가치가 있습니다:

```jldoctest
julia> NaN == NaN
false

julia> NaN != NaN
true

julia> NaN < NaN
false

julia> NaN > NaN
false
```

그리고 [arrays](@ref man-multi-dim-arrays) 작업 시 두통을 유발할 수 있습니다:

```jldoctest
julia> [1 NaN] == [1 NaN]
false
```

줄리아는 해시 키 비교와 같은 상황에서 유용할 수 있는 특별한 값에 대한 숫자를 테스트하는 추가 기능을 제공합니다:

| Function                | Tests if                  |
|:----------------------- |:------------------------- |
| [`isequal(x, y)`](@ref) | `x` and `y` are identical |
| [`isfinite(x)`](@ref)   | `x` is a finite number    |
| [`isinf(x)`](@ref)      | `x` is infinite           |
| [`isnan(x)`](@ref)      | `x` is not a number       |

[`isequal`](@ref)는 `NaN`을 서로 같다고 간주합니다:

```jldoctest
julia> isequal(NaN, NaN)
true

julia> isequal([1 NaN], [1 NaN])
true

julia> isequal(NaN, NaN32)
true
```

`isequal`은 부호가 있는 0을 구분하는 데에도 사용할 수 있습니다:

```jldoctest
julia> -0.0 == 0.0
true

julia> isequal(-0.0, 0.0)
false
```

부호가 있는 정수, 부호가 없는 정수 및 부동 소수점 수 간의 혼합형 비교는 까다로울 수 있습니다. Julia가 이를 올바르게 수행하도록 많은 주의가 기울여졌습니다.

다른 유형의 경우, `isequal`은 기본적으로 [`==`](@ref)를 호출하므로, 자신의 유형에 대한 동등성을 정의하려면 `4d61726b646f776e2e436f64652822222c20223d3d2229_40726566` 메서드만 추가하면 됩니다. 자신의 동등성 함수를 정의하는 경우, `isequal(x,y)`가 `hash(x) == hash(y)`를 의미하도록 보장하기 위해 해당하는 [`hash`](@ref) 메서드를 정의하는 것이 좋습니다.

### Chaining comparisons

대부분의 언어와 달리, [notable exception of Python](https://en.wikipedia.org/wiki/Python_syntax_and_semantics#Comparison_operators)에서는 비교를 임의로 연결할 수 있습니다:

```jldoctest
julia> 1 < 2 <= 2 < 3 == 3 > 2 >= 1 == 1 < 3 != 5
true
```

비교를 연결하는 것은 수치 코드에서 종종 매우 편리합니다. 연결된 비교는 스칼라 비교를 위해 `&&` 연산자를 사용하고, 배열에서 작동할 수 있도록 요소별 비교를 위해 [`&`](@ref) 연산자를 사용합니다. 예를 들어, `0 .< A .< 1`은 `A`의 해당 요소가 0과 1 사이에 있을 때 true인 불리언 배열을 제공합니다.

체인 비교의 평가 동작에 유의하세요:

```jldoctest
julia> v(x) = (println(x); x)
v (generic function with 1 method)

julia> v(1) < v(2) <= v(3)
2
1
3
true

julia> v(1) > v(2) <= v(3)
2
1
false
```

중간 표현식은 `v(1) < v(2) && v(2) <= v(3)`와 같이 표현했을 경우 두 번 평가되는 것이 아니라 한 번만 평가됩니다. 그러나 체인 비교에서 평가 순서는 정의되어 있지 않습니다. 부작용(예: 출력)이 있는 표현식을 체인 비교에서 사용하는 것은 강력히 권장되지 않습니다. 부작용이 필요한 경우, 단축 평가 `&&` 연산자를 명시적으로 사용해야 합니다(참조: [Short-Circuit Evaluation](@ref)).

### Elementary Functions

줄리아는 수학 함수와 연산자의 포괄적인 컬렉션을 제공합니다. 이러한 수학 연산은 정수, 부동 소수점 숫자, 유리수 및 복소수 등 의미 있는 정의를 허용하는 가능한 넓은 범위의 수치 값에 대해 정의됩니다. 이러한 정의가 의미가 있는 곳이라면 어디에서나 적용됩니다.

또한 이러한 함수(모든 Julia 함수와 마찬가지로)는 [dot syntax](@ref man-vectorized) `f.(A)`를 사용하여 배열 및 기타 컬렉션에 "벡터화" 방식으로 적용될 수 있습니다. 예를 들어, `sin.(A)`는 배열 `A`의 각 요소의 사인을 계산합니다.

## Operator Precedence and Associativity

줄리아는 다음과 같은 연산의 순서와 결합법칙을 적용합니다. 가장 높은 우선순위에서 가장 낮은 우선순위까지:

| Category       | Operators                                              | Associativity   |
|:-------------- |:------------------------------------------------------ |:--------------- |
| Syntax         | `.` followed by `::`                                   | Left            |
| Exponentiation | `^`                                                    | Right           |
| Unary          | `+ - ! ~ ¬ √ ∛ ∜ ⋆ ± ∓ <: >:`                          | Right[^1]       |
| Bitshifts      | `<< >> >>>`                                            | Left            |
| Fractions      | `//`                                                   | Left            |
| Multiplication | `* / % & \ ÷`                                          | Left[^2]        |
| Addition       | `+ - \| ⊻`                                             | Left[^2]        |
| Syntax         | `: ..`                                                 | Left            |
| Syntax         | `\|>`                                                  | Left            |
| Syntax         | `<\|`                                                  | Right           |
| Comparisons    | `> < >= <= == === != !== <:`                           | Non-associative |
| Control flow   | `&&` followed by `\|\|` followed by `?`                | Right           |
| Pair           | `=>`                                                   | Right           |
| Assignments    | `= += -= *= /= //= \= ^= ÷= %= \|= &= ⊻= <<= >>= >>>=` | Right           |

[^1]: The unary operators `+` and `-` require explicit parentheses around their argument to disambiguate them from the operator `++`, etc. Other compositions of unary operators are parsed with right-associativity, e. g., `√√-a` as `√(√(-a))`.

[^2]: The operators `+`, `++` and `*` are non-associative. `a + b + c` is parsed as `+(a, b, c)` not `+(+(a, b), c)`. However, the fallback methods for `+(a, b, c, d...)` and `*(a, b, c, d...)` both default to left-associative evaluation.

모든 Julia 연산자의 우선 순위에 대한 완전한 목록은 이 파일의 맨 위를 참조하세요: [`src/julia-parser.scm`](https://github.com/JuliaLang/julia/blob/master/src/julia-parser.scm). 거기에서 일부 연산자는 `Base` 모듈에 정의되어 있지 않지만 표준 라이브러리, 패키지 또는 사용자 코드에 의해 정의될 수 있습니다.

주어진 연산자에 대한 수치적 우선 순위는 내장 함수 `Base.operator_precedence`를 통해 찾을 수 있으며, 더 높은 숫자가 우선 순위를 가집니다:

```jldoctest
julia> Base.operator_precedence(:+), Base.operator_precedence(:*), Base.operator_precedence(:.)
(11, 12, 17)

julia> Base.operator_precedence(:sin), Base.operator_precedence(:+=), Base.operator_precedence(:(=))  # (Note the necessary parens on `:(=)`)
(0, 1, 1)
```

연산자 결합성을 나타내는 기호는 내장 함수 `Base.operator_associativity`를 호출하여 찾을 수 있습니다:

```jldoctest
julia> Base.operator_associativity(:-), Base.operator_associativity(:+), Base.operator_associativity(:^)
(:left, :none, :right)

julia> Base.operator_associativity(:⊗), Base.operator_associativity(:sin), Base.operator_associativity(:→)
(:left, :none, :right)
```

`:sin`와 같은 기호는 우선 순위 `0`을 반환합니다. 이 값은 유효하지 않은 연산자를 나타내며 최저 우선 순위의 연산자를 나타내지 않습니다. 마찬가지로, 이러한 연산자는 결합성 `:none`이 할당됩니다.

[Numeric literal coefficients](@ref man-numeric-literal-coefficients)와 같은 `2x`는 다른 이진 연산보다 우선 순위가 높은 곱셈으로 처리되며, `^`의 경우 지수로서만 더 높은 우선 순위를 가집니다.

```jldoctest
julia> x = 3; 2x^2
18

julia> x = 3; 2^2x
64
```

대조는 단항 연산자처럼 구문 분석되며, 지수 주위에서 동일한 자연 비대칭성을 가집니다: `-x^y`와 `2x^y`는 각각 `-(x^y)`와 `2(x^y)`로 구문 분석되는 반면, `x^-y`와 `x^2y`는 각각 `x^(-y)`와 `x^(2y)`로 구문 분석됩니다.

## Numerical Conversions

줄리아는 부정확한 변환 처리 방식이 다른 세 가지 형태의 숫자 변환을 지원합니다.

  * 표기법 `T(x)` 또는 `convert(T, x)`는 `x`를 타입 `T`의 값으로 변환합니다.

      * `T`가 부동 소수점 타입인 경우, 결과는 표현 가능한 가장 가까운 값이며, 이는 양의 무한대 또는 음의 무한대일 수 있습니다.
      * `T`가 정수형일 경우, `x`가 `T`로 표현될 수 없으면 `InexactError`가 발생합니다.
  * `x % T`는 정수 `x`를 `T`의 정수형 값으로 변환하며, 이는 `x`를 `2^n`으로 나눈 나머지와 동치입니다. 여기서 `n`은 `T`의 비트 수입니다. 다시 말해, 이진 표현이 맞도록 잘립니다.
  * [Rounding functions](@ref)는 선택적 인수로 타입 `T`를 받습니다. 예를 들어, `round(Int,x)`는 `Int(round(x))`의 약어입니다.

다음 예시는 다양한 형태를 보여줍니다.

```jldoctest
julia> Int8(127)
127

julia> Int8(128)
ERROR: InexactError: trunc(Int8, 128)
Stacktrace:
[...]

julia> Int8(127.0)
127

julia> Int8(3.14)
ERROR: InexactError: Int8(3.14)
Stacktrace:
[...]

julia> Int8(128.0)
ERROR: InexactError: Int8(128.0)
Stacktrace:
[...]

julia> 127 % Int8
127

julia> 128 % Int8
-128

julia> round(Int8,127.4)
127

julia> round(Int8,127.6)
ERROR: InexactError: Int8(128.0)
Stacktrace:
[...]
```

[Conversion and Promotion](@ref conversion-and-promotion)를 참조하여 자신만의 변환 및 프로모션을 정의하는 방법을 확인하세요.

### Rounding functions

| Function              | Description                      | Return type |
|:--------------------- |:-------------------------------- |:----------- |
| [`round(x)`](@ref)    | round `x` to the nearest integer | `typeof(x)` |
| [`round(T, x)`](@ref) | round `x` to the nearest integer | `T`         |
| [`floor(x)`](@ref)    | round `x` towards `-Inf`         | `typeof(x)` |
| [`floor(T, x)`](@ref) | round `x` towards `-Inf`         | `T`         |
| [`ceil(x)`](@ref)     | round `x` towards `+Inf`         | `typeof(x)` |
| [`ceil(T, x)`](@ref)  | round `x` towards `+Inf`         | `T`         |
| [`trunc(x)`](@ref)    | round `x` towards zero           | `typeof(x)` |
| [`trunc(T, x)`](@ref) | round `x` towards zero           | `T`         |

### Division functions

| Function                   | Description                                                                                               |
|:-------------------------- |:--------------------------------------------------------------------------------------------------------- |
| [`div(x, y)`](@ref), `x÷y` | truncated division; quotient rounded towards zero                                                         |
| [`fld(x, y)`](@ref)        | floored division; quotient rounded towards `-Inf`                                                         |
| [`cld(x, y)`](@ref)        | ceiling division; quotient rounded towards `+Inf`                                                         |
| [`rem(x, y)`](@ref), `x%y` | remainder; satisfies `x == div(x, y)*y + rem(x, y)`; sign matches `x`                                     |
| [`mod(x, y)`](@ref)        | modulus; satisfies `x == fld(x, y)*y + mod(x, y)`; sign matches `y`                                       |
| [`mod1(x, y)`](@ref)       | `mod` with offset 1; returns `r∈(0, y]` for `y>0` or `r∈[y, 0)` for `y<0`, where `mod(r, y) == mod(x, y)` |
| [`mod2pi(x)`](@ref)        | modulus with respect to 2pi;  `0 <= mod2pi(x) < 2pi`                                                      |
| [`divrem(x, y)`](@ref)     | returns `(div(x, y),rem(x, y))`                                                                           |
| [`fldmod(x, y)`](@ref)     | returns `(fld(x, y), mod(x, y))`                                                                          |
| [`gcd(x, y...)`](@ref)     | greatest positive common divisor of `x`, `y`,...                                                          |
| [`lcm(x, y...)`](@ref)     | least positive common multiple of `x`, `y`,...                                                            |

### Sign and absolute value functions

| Function                 | Description                                                |
|:------------------------ |:---------------------------------------------------------- |
| [`abs(x)`](@ref)         | a positive value with the magnitude of `x`                 |
| [`abs2(x)`](@ref)        | the squared magnitude of `x`                               |
| [`sign(x)`](@ref)        | indicates the sign of `x`, returning -1, 0, or +1          |
| [`signbit(x)`](@ref)     | indicates whether the sign bit is on (true) or off (false) |
| [`copysign(x, y)`](@ref) | a value with the magnitude of `x` and the sign of `y`      |
| [`flipsign(x, y)`](@ref) | a value with the magnitude of `x` and the sign of `x*y`    |

### Powers, logs and roots

| Function                 | Description                                                                |
|:------------------------ |:-------------------------------------------------------------------------- |
| [`sqrt(x)`](@ref), `√x`  | square root of `x`                                                         |
| [`cbrt(x)`](@ref), `∛x`  | cube root of `x`                                                           |
| [`hypot(x, y)`](@ref)    | hypotenuse of right-angled triangle with other sides of length `x` and `y` |
| [`exp(x)`](@ref)         | natural exponential function at `x`                                        |
| [`expm1(x)`](@ref)       | accurate `exp(x) - 1` for `x` near zero                                    |
| [`ldexp(x, n)`](@ref)    | `x * 2^n` computed efficiently for integer values of `n`                   |
| [`log(x)`](@ref)         | natural logarithm of `x`                                                   |
| [`log(b, x)`](@ref)      | base `b` logarithm of `x`                                                  |
| [`log2(x)`](@ref)        | base 2 logarithm of `x`                                                    |
| [`log10(x)`](@ref)       | base 10 logarithm of `x`                                                   |
| [`log1p(x)`](@ref)       | accurate `log(1 + x)` for `x` near zero                                    |
| [`exponent(x)`](@ref)    | binary exponent of `x`                                                     |
| [`significand(x)`](@ref) | binary significand (a.k.a. mantissa) of a floating-point number `x`        |

[`hypot`](@ref), [`expm1`](@ref), 및 [`log1p`](@ref)와 같은 함수가 왜 필요하고 유용한지에 대한 개요는 John D. Cook의 훌륭한 블로그 포스트 두 편을 참조하세요: [expm1, log1p, erfc](https://www.johndcook.com/blog/2010/06/07/math-library-functions-that-seem-unnecessary/) 및 [hypot](https://www.johndcook.com/blog/2010/06/02/whats-so-hard-about-finding-a-hypotenuse/).

### Trigonometric and hyperbolic functions

모든 표준 삼각 함수와 쌍곡선 함수도 정의됩니다:

```
sin    cos    tan    cot    sec    csc
sinh   cosh   tanh   coth   sech   csch
asin   acos   atan   acot   asec   acsc
asinh  acosh  atanh  acoth  asech  acsch
sinc   cosc
```

이것들은 모두 단일 인수를 받는 함수이며, [`atan`](@ref)는 전통적인 [`atan2`](https://en.wikipedia.org/wiki/Atan2) 함수에 해당하는 두 개의 인수도 허용합니다.

추가적으로, [`sinpi(x)`](@ref)와 [`cospi(x)`](@ref)는 각각 [`sin(pi * x)`](@ref)와 [`cos(pi * x)`](@ref)의 보다 정확한 계산을 위해 제공됩니다.

각도를 라디안 대신 사용하여 삼각 함수를 계산하려면 함수 뒤에 `d`를 붙입니다. 예를 들어, [`sind(x)`](@ref)는 `x`가 각도로 지정된 경우 `x`의 사인 값을 계산합니다. 각도 변형이 있는 삼각 함수의 전체 목록은 다음과 같습니다:

```
sind   cosd   tand   cotd   secd   cscd
asind  acosd  atand  acotd  asecd  acscd
```

### Special functions

패키지 [SpecialFunctions.jl](https://github.com/JuliaMath/SpecialFunctions.jl)에서 제공하는 많은 다른 특별한 수학 함수가 있습니다.
