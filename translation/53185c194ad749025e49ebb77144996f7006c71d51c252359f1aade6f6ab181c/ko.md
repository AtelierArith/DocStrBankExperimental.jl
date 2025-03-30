# [Variables](@id man-variables)

변수는 Julia에서 값에 연결(또는 바인딩)된 이름입니다. 이는 나중에 사용할 값을 저장하고 싶을 때 유용합니다(예를 들어, 어떤 수학을 통해 얻은 값). 예를 들어:

```julia-repl
# Assign the value 10 to the variable x
julia> x = 10
10

# Doing math with x's value
julia> x + 1
11

# Reassign x's value
julia> x = 1 + 1
2

# You can assign values of other types, like strings of text
julia> x = "Hello World!"
"Hello World!"
```

줄리아는 변수 이름을 지정하는 데 매우 유연한 시스템을 제공합니다. 변수 이름은 대소문자를 구분하며, 의미론적 의미가 없습니다(즉, 언어는 변수 이름에 따라 변수를 다르게 취급하지 않습니다).

```jldoctest
julia> x = 1.0
1.0

julia> y = -3
-3

julia> Z = "My string"
"My string"

julia> customary_phrase = "Hello world!"
"Hello world!"

julia> UniversalDeclarationOfHumanRightsStart = "人人生而自由，在尊严和权利上一律平等。"
"人人生而自由，在尊严和权利上一律平等。"
```

유니코드 이름(UTF-8 인코딩)은 허용됩니다:

```jldoctest
julia> δ = 0.00001
1.0e-5

julia> 안녕하세요 = "Hello"
"Hello"
```

Julia REPL 및 여러 다른 Julia 편집 환경에서는 백슬래시가 있는 LaTeX 기호 이름을 입력한 후 탭을 눌러 많은 유니코드 수학 기호를 입력할 수 있습니다. 예를 들어, 변수 이름 `δ`는 `\delta`-*탭*을 입력하여 입력할 수 있으며, 심지어 `α̂⁽²⁾`는 `\alpha`-*탭*-`\hat`-*탭*-`\^(2)`-*탭*으로 입력할 수 있습니다. (어디선가 기호를 찾았는데, 예를 들어 다른 사람의 코드에서, 입력 방법을 모를 경우 REPL 도움말이 알려줍니다: 그냥 `?`를 입력한 다음 기호를 붙여넣기만 하면 됩니다.)

줄리아는 기존의 내보낸 상수와 함수를 로컬로 덮어쓰는 것을 허용합니다(하지만 잠재적인 혼란을 피하기 위해 권장되지 않습니다):

```jldoctest; filter = r"with \d+ methods"
julia> pi = 3
3

julia> pi
3

julia> sqrt = 4
4

julia> length() = 5
length (generic function with 1 method)

julia> Base.length
length (generic function with 79 methods)
```

그러나 이미 사용 중인 내장 상수나 함수를 재정의하려고 하면, Julia는 오류를 발생시킵니다:

```jldoctest
julia> pi
π = 3.1415926535897...

julia> pi = 3
ERROR: cannot assign a value to imported variable Base.pi from module Main

julia> sqrt(100)
10.0

julia> sqrt = 4
ERROR: cannot assign a value to imported variable Base.sqrt from module Main
```

## [Allowed Variable Names](@id man-allowed-variable-names)

변수 이름은 문자(A-Z 또는 a-z), 밑줄 또는 00A0보다 큰 유니코드 코드 포인트의 하위 집합으로 시작해야 합니다. 특히, [Unicode character categories](https://www.fileformat.info/info/unicode/category/index.htm) Lu/Ll/Lt/Lm/Lo/Nl(문자), Sc/So(통화 및 기타 기호) 및 몇 가지 다른 문자와 유사한 문자(예: Sm 수학 기호의 하위 집합)가 허용됩니다. 이후 문자는 ! 및 숫자(0-9 및 Nd/No 범주의 기타 문자)를 포함할 수 있으며, 기타 유니코드 코드 포인트: 발음 기호 및 기타 수정 기호(범주 Mn/Mc/Me/Sk), 일부 구두점 연결자(범주 Pc), 프라임 및 몇 가지 다른 문자를 포함할 수 있습니다.

연산자 `+`와 같은 기호는 유효한 식별자이지만 특별하게 파싱됩니다. 일부 맥락에서는 연산자를 변수처럼 사용할 수 있습니다. 예를 들어, `(+)`는 덧셈 함수를 참조하며, `(+) = f`는 이를 재할당합니다. 대부분의 유니코드 중위 연산자(카테고리 Sm에 속하는)인 `⊕`는 중위 연산자로 파싱되며 사용자 정의 메서드에 사용할 수 있습니다(예: `const ⊗ = kron`을 사용하여 `⊗`를 중위 크로네커 곱으로 정의할 수 있습니다). 연산자는 수정 기호, 프라임 및 아래/위 첨자와 함께 접미사로 사용할 수도 있습니다. 예를 들어, `+̂ₐ″`는 `+`와 동일한 우선 순위를 가진 중위 연산자로 파싱됩니다. 아래 첨자/위 첨자 문자로 끝나는 연산자와 이후 변수 이름 사이에는 공백이 필요합니다. 예를 들어, `+ᵃ`가 연산자라면 `+ᵃx`는 `+ᵃ x`로 작성해야 하며, 이는 `+ ᵃx`와 구별됩니다. 여기서 `ᵃx`는 변수 이름입니다.

특정 변수 이름 클래스는 오직 언더스코어만 포함된 것입니다. 이러한 식별자는 쓰기 전용입니다. 즉, 값만 할당할 수 있으며, 즉시 버려지고, 그 값은 어떤 방식으로도 사용할 수 없습니다.

```julia-repl
julia> x, ___ = size([2 2; 1 1])
(2, 2)

julia> y = ___
ERROR: syntax: all-underscore identifiers are write-only and their values cannot be used in expressions

julia> println(___)
ERROR: syntax: all-underscore identifiers are write-only and their values cannot be used in expressions
```

The only explicitly disallowed names for variables are the names of the built-in [Keywords](@ref Keywords):

```julia-repl
julia> else = false
ERROR: syntax: unexpected "else"

julia> try = "No"
ERROR: syntax: unexpected "="
```

일부 유니코드 문자는 식별자에서 동등한 것으로 간주됩니다. 유니코드 결합 문자를 입력하는 다양한 방법(예: 악센트)은 동등한 것으로 처리됩니다(특히, 줄리아 식별자는 [NFC](https://en.wikipedia.org/wiki/Unicode_equivalence)입니다). 줄리아는 또한 시각적으로 유사하고 일부 입력 방법으로 쉽게 입력할 수 있는 문자에 대해 몇 가지 비표준 동등성을 포함합니다. 유니코드 문자 `ɛ` (U+025B: 라틴 소문자 열린 e)와 `µ` (U+00B5: 마이크로 기호)는 해당 그리스 문자와 동등한 것으로 처리됩니다. 중간 점 `·` (U+00B7)과 그리스 [interpunct](https://en.wikipedia.org/wiki/Interpunct) `·` (U+0387) 모두 수학적 점 연산자 `⋅` (U+22C5)로 처리됩니다. 빼기 기호 `−` (U+2212)는 하이픈-마이너스 기호 `-` (U+002D)와 동등한 것으로 처리됩니다.

## [Assignment expressions and assignment versus mutation](@id man-assignment-expressions)

할당 `variable = value`는 이름 `variable`을 오른쪽에 계산된 `value`에 "바인딩"하며, 전체 할당은 Julia에 의해 오른쪽의 `value`와 같은 표현식으로 처리됩니다. 이는 할당이 *체인*될 수 있음을 의미합니다(같은 `value`가 여러 변수에 `variable1 = variable2 = value`로 할당됨) 또는 다른 표현식에서 사용될 수 있으며, 이로 인해 REPL에서 그 결과가 오른쪽의 값으로 표시됩니다. (일반적으로 REPL은 평가한 표현식의 값을 표시합니다.) 예를 들어, 여기서 `b = 2+2`의 값 `4`가 다른 산술 연산 및 할당에 사용됩니다:

```jldoctest
julia> a = (b = 2+2) + 3
7

julia> a
7

julia> b
4
```

일반적인 혼란은 *할당* (값에 새로운 "이름"을 부여하는 것)과 *변경* (값을 변경하는 것) 사이의 구분입니다. `a = 2`를 실행한 후 `a = 3`을 실행하면, "이름" `a`가 새로운 값 `3`을 가리키도록 변경된 것입니다 … 숫자 `2`는 변경되지 않았으므로 `2+2`는 여전히 `4`를 반환하고 `6`이 아닙니다! 이 구분은 [arrays](@ref lib-arrays)와 같은 *변경 가능한* 유형을 다룰 때 더 명확해집니다. 그 내용은 *변경*될 수 있습니다:

```jldoctest mutation_vs_rebind
julia> a = [1,2,3] # an array of 3 integers
3-element Vector{Int64}:
 1
 2
 3

julia> b = a   # both b and a are names for the same array!
3-element Vector{Int64}:
 1
 2
 3
```

여기서 `b = a`라는 줄은 배열 `a`의 복사본을 만들지 않고, 단순히 이름 `b`를 *같은* 배열 `a`에 바인딩합니다: `b`와 `a`는 모두 메모리의 하나의 배열 `[1,2,3]`를 "가리킵니다". 반면에, 할당 `a[i] = value`는 배열의 *내용*을 *변경*하며, 수정된 배열은 이름 `a`와 `b`를 통해 모두 볼 수 있습니다:

```jldoctest mutation_vs_rebind
julia> a[1] = 42     # change the first element
42

julia> a = 3.14159   # a is now the name of a different object
3.14159

julia> b   # b refers to the original array object, which has been mutated
3-element Vector{Int64}:
 42
  2
  3
```

즉, `a[i] = value` (즉, [`setindex!`](@ref)의 별칭)은 메모리에서 기존 배열 객체를 *변경*하며, 이는 `a` 또는 `b`를 통해 접근할 수 있습니다. 이후 `a = 3.14159`를 설정해도 이 배열은 변경되지 않으며, 단순히 `a`를 다른 객체에 바인딩합니다; 배열은 여전히 `b`를 통해 접근할 수 있습니다. 기존 객체를 변경하는 또 다른 일반적인 구문은 `a.field = value` (즉, [`setproperty!`](@ref)의 별칭)로, 이는 [`mutable struct`](@ref)를 변경하는 데 사용할 수 있습니다. 점 할당을 통한 변경도 있으며, 예를 들어 `b .= 5:7` (이는 배열 `b`를 제자리에서 `[5,6,7]`을 포함하도록 변경합니다)와 같은 방식으로, 이는 Julia의 [vectorized "dot" syntax](@ref man-dot-operators)의 일환입니다.

When you call a [function](@ref man-functions) in Julia, it behaves as if you *assigned* the argument values to new variable names corresponding to the function arguments, as discussed in [Argument-Passing Behavior](@ref man-argument-passing).  (By [convention](@ref man-punctuation), functions that mutate one or more of their arguments have names ending with `!`.)

## Stylistic Conventions

줄리아는 유효한 이름에 대해 몇 가지 제한을 두지만, 다음과 같은 규칙을 채택하는 것이 유용해졌습니다:

  * 변수의 이름은 소문자로 되어 있습니다.
  * 단어 구분은 밑줄(`'_'`)로 표시할 수 있지만, 이름이 그렇지 않으면 읽기 어려운 경우를 제외하고는 밑줄 사용을 권장하지 않습니다.
  * `Type`와 `Module`의 이름은 대문자로 시작하며, 단어 구분은 언더스코어 대신 대문자 카멜 케이스로 표시됩니다.
  * `function`과 `macro`의 이름은 소문자로, 언더스코어 없이 작성합니다.
  * 인수에 쓰는 함수를 `!`로 끝나는 이름을 가집니다. 이러한 함수는 "변형" 또는 "제자리" 함수라고도 불리며, 함수가 호출된 후 인수에 변화를 일으키도록 설계되었으며, 단순히 값을 반환하는 것이 아닙니다.

스타일 규약에 대한 자세한 내용은 [Style Guide](@ref)을 참조하세요.
