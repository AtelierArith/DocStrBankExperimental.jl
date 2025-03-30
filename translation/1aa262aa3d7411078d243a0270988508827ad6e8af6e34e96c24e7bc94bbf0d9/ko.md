# [Strings](@id man-strings)

문자열은 유한한 문자 시퀀스입니다. 물론, 진짜 문제는 문자가 무엇인지 묻는 것입니다. 영어 사용자가 익숙한 문자는 `A`, `B`, `C` 등과 숫자 및 일반적인 구두점 기호입니다. 이러한 문자는 [ASCII](https://en.wikipedia.org/wiki/ASCII) 표준에 의해 0에서 127 사이의 정수 값으로 매핑되는 방식으로 표준화되어 있습니다. 물론, 비영어권 언어에서 사용되는 많은 다른 문자도 있으며, 여기에는 악센트와 기타 수정이 가해진 ASCII 문자 변형, 키릴 문자 및 그리스어와 같은 관련 스크립트, 아랍어, 중국어, 히브리어, 힌디어, 일본어 및 한국어와 같이 ASCII 및 영어와 완전히 관련이 없는 스크립트가 포함됩니다. [Unicode](https://en.wikipedia.org/wiki/Unicode) 표준은 문자가 정확히 무엇인지에 대한 복잡성을 다루며, 일반적으로 이 문제를 해결하는 결정적인 표준으로 받아들여집니다. 필요에 따라 이러한 복잡성을 완전히 무시하고 오직 ASCII 문자만 존재한다고 가정할 수도 있고, 비ASCII 텍스트를 처리할 때 마주칠 수 있는 모든 문자나 인코딩을 처리할 수 있는 코드를 작성할 수도 있습니다. Julia는 일반 ASCII 텍스트를 간단하고 효율적으로 처리할 수 있게 해주며, 유니코드를 처리하는 것도 가능한 한 간단하고 효율적입니다. 특히, C 스타일 문자열 코드를 작성하여 ASCII 문자열을 처리할 수 있으며, 성능과 의미 측면에서 예상대로 작동합니다. 만약 이러한 코드가 비ASCII 텍스트를 만나면, 명확한 오류 메시지와 함께 우아하게 실패하며, 조용히 손상된 결과를 도입하지 않습니다. 이러한 일이 발생하면, 비ASCII 데이터를 처리하도록 코드를 수정하는 것은 간단합니다.

Julia의 문자열에 대한 몇 가지 주목할 만한 고급 기능이 있습니다:

  * Julia에서 문자열(및 문자열 리터럴)에 사용되는 내장 콘크리트 타입은 [`String`](@ref)입니다. 이는 [Unicode](https://en.wikipedia.org/wiki/Unicode) 문자의 전체 범위를 [UTF-8](https://en.wikipedia.org/wiki/UTF-8) 인코딩을 통해 지원합니다. (다른 유니코드 인코딩으로 변환하기 위해 [`transcode`](@ref) 함수가 제공됩니다.)
  * 모든 문자열 유형은 추상 유형 `AbstractString`의 하위 유형이며, 외부 패키지는 추가적인 `AbstractString` 하위 유형을 정의합니다(예: 다른 인코딩을 위한). 문자열 인수를 기대하는 함수를 정의할 경우, 모든 문자열 유형을 수용하기 위해 유형을 `AbstractString`으로 선언해야 합니다.
  * C와 Java와 마찬가지로, 그러나 대부분의 동적 언어와는 달리, Julia는 단일 문자를 나타내기 위한 1급 타입인 [`AbstractChar`](@ref)를 가지고 있습니다. 내장된 [`Char`](@ref)의 하위 타입인 `AbstractChar`는 모든 유니코드 문자를 나타낼 수 있는 32비트 원시 타입입니다(UTF-8 인코딩을 기반으로 함).
  * Java와 마찬가지로 문자열은 변경할 수 없습니다: `AbstractString` 객체의 값은 변경할 수 없습니다. 다른 문자열 값을 구성하려면 다른 문자열의 일부로부터 새 문자열을 구성해야 합니다.
  * 개념적으로, 문자열은 인덱스에서 문자로의 *부분 함수*입니다: 일부 인덱스 값에 대해서는 문자 값이 반환되지 않고 대신 예외가 발생합니다. 이는 인코딩된 표현의 바이트 인덱스를 사용하여 문자열에 효율적으로 인덱싱할 수 있게 해주며, 이는 가변 길이 인코딩의 유니코드 문자열에 대해 효율적이고 간단하게 구현할 수 없습니다.

## [Characters](@id man-characters)

`Char` 값은 단일 문자를 나타냅니다: 이는 특별한 리터럴 표현과 적절한 산술 동작을 가진 32비트 원시 타입일 뿐이며, [Unicode code point](https://en.wikipedia.org/wiki/Code_point)를 나타내는 숫자 값으로 변환될 수 있습니다. (Julia 패키지는 다른 [text encodings](https://en.wikipedia.org/wiki/Character_encoding)에 대한 작업을 최적화하기 위해 `AbstractChar`의 다른 하위 유형을 정의할 수 있습니다.) `Char` 값이 입력되고 표시되는 방법은 다음과 같습니다 (문자 리터럴은 큰따옴표가 아닌 작은따옴표로 구분된다는 점에 유의하십시오):

```jldoctest
julia> c = 'x'
'x': ASCII/Unicode U+0078 (category Ll: Letter, lowercase)

julia> typeof(c)
Char
```

`Char`를 쉽게 정수 값, 즉 코드 포인트로 변환할 수 있습니다:

```jldoctest
julia> c = Int('x')
120

julia> typeof(c)
Int64
```

32비트 아키텍처에서는 [`typeof(c)`](@ref)가 [`Int32`](@ref)가 됩니다. 정수 값을 `Char`로 쉽게 변환할 수 있습니다:

```jldoctest
julia> Char(120)
'x': ASCII/Unicode U+0078 (category Ll: Letter, lowercase)
```

모든 정수 값이 유효한 유니코드 코드 포인트는 아니지만, 성능을 위해 `Char` 변환은 모든 문자 값이 유효한지 확인하지 않습니다. 변환된 각 값이 유효한 코드 포인트인지 확인하려면 [`isvalid`](@ref) 함수를 사용하세요:

```jldoctest
julia> Char(0x110000)
'\U110000': Unicode U+110000 (category In: Invalid, too high)

julia> isvalid(Char, 0x110000)
false
```

이 글을 작성하는 시점에서 유효한 유니코드 코드 포인트는 `U+0000`에서 `U+D7FF` 및 `U+E000`에서 `U+10FFFF`까지입니다. 이들은 아직 모두 이해할 수 있는 의미가 부여되지 않았으며, 반드시 애플리케이션에서 해석될 수 있는 것은 아니지만, 이 모든 값은 유효한 유니코드 문자로 간주됩니다.

단일 따옴표 안에 유니코드 문자를 입력할 수 있습니다. `\u` 다음에 최대 네 개의 16진수 숫자 또는 `\U` 다음에 최대 여덟 개의 16진수 숫자를 사용합니다(가장 긴 유효 값은 최대 여섯 개만 필요합니다):

```jldoctest
julia> '\u0'
'\0': ASCII/Unicode U+0000 (category Cc: Other, control)

julia> '\u78'
'x': ASCII/Unicode U+0078 (category Ll: Letter, lowercase)

julia> '\u2200'
'∀': Unicode U+2200 (category Sm: Symbol, math)

julia> '\U10ffff'
'\U10ffff': Unicode U+10FFFF (category Cn: Other, not assigned)
```

줄리아는 시스템의 로케일 및 언어 설정을 사용하여 어떤 문자를 그대로 출력할 수 있는지, 어떤 문자는 일반적인 이스케이프 `\u` 또는 `\U` 입력 형식을 사용하여 출력해야 하는지를 결정합니다. 이러한 유니코드 이스케이프 형식 외에도 [C's traditional escaped input forms](https://en.wikipedia.org/wiki/C_syntax#Backslash_escapes)도 사용할 수 있습니다:

```jldoctest
julia> Int('\0')
0

julia> Int('\t')
9

julia> Int('\n')
10

julia> Int('\e')
27

julia> Int('\x7f')
127

julia> Int('\177')
127
```

`Char` 값으로 비교 및 제한된 양의 산술 연산을 수행할 수 있습니다:

```jldoctest
julia> 'A' < 'a'
true

julia> 'A' <= 'a' <= 'Z'
false

julia> 'A' <= 'X' <= 'Z'
true

julia> 'x' - 'a'
23

julia> 'A' + 1
'B': ASCII/Unicode U+0042 (category Lu: Letter, uppercase)
```

## String Basics

문자열 리터럴은 큰따옴표 또는 세 개의 큰따옴표(작은따옴표 아님)로 구분됩니다:

```jldoctest helloworldstring
julia> str = "Hello, world.\n"
"Hello, world.\n"

julia> """Contains "quote" characters"""
"Contains \"quote\" characters"
```

문자열의 긴 줄은 줄 바꿈 앞에 백슬래시(`\`)를 추가하여 나눌 수 있습니다:

```jldoctest
julia> "This is a long \
       line"
"This is a long line"
```

문자열에서 문자를 추출하려면, 인덱스를 사용합니다:

```jldoctest helloworldstring
julia> str[begin]
'H': ASCII/Unicode U+0048 (category Lu: Letter, uppercase)

julia> str[1]
'H': ASCII/Unicode U+0048 (category Lu: Letter, uppercase)

julia> str[6]
',': ASCII/Unicode U+002C (category Po: Punctuation, other)

julia> str[end]
'\n': ASCII/Unicode U+000A (category Cc: Other, control)
```

많은 Julia 객체, 문자열을 포함하여, 정수로 인덱싱할 수 있습니다. 첫 번째 요소(문자열의 첫 번째 문자)의 인덱스는 [`firstindex(str)`](@ref)로 반환되며, 마지막 요소(문자)의 인덱스는 [`lastindex(str)`](@ref)로 반환됩니다. 키워드 `begin`과 `end`는 주어진 차원에 따라 각각 첫 번째 및 마지막 인덱스의 약어로 인덱싱 작업 내에서 사용할 수 있습니다. 문자열 인덱싱은 Julia의 대부분의 인덱싱과 마찬가지로 1 기반입니다: `firstindex`는 항상 어떤 `AbstractString`에 대해서도 `1`을 반환합니다. 그러나 아래에서 볼 수 있듯이, `lastindex(str)`는 문자열에 대해 일반적으로 `length(str)`과 같지 않습니다. 왜냐하면 일부 유니코드 문자는 여러 "코드 유닛"을 차지할 수 있기 때문입니다.

[`end`](@ref)와 같은 일반 값처럼 산술 및 기타 연산을 수행할 수 있습니다:

```jldoctest helloworldstring
julia> str[end-1]
'.': ASCII/Unicode U+002E (category Po: Punctuation, other)

julia> str[end÷2]
' ': ASCII/Unicode U+0020 (category Zs: Separator, space)
```

`begin`(`1`)보다 작은 인덱스나 `end`보다 큰 인덱스를 사용하면 오류가 발생합니다:

```jldoctest helloworldstring
julia> str[begin-1]
ERROR: BoundsError: attempt to access 14-codeunit String at index [0]
[...]

julia> str[end+1]
ERROR: BoundsError: attempt to access 14-codeunit String at index [15]
[...]
```

범위 인덱싱을 사용하여 부분 문자열을 추출할 수도 있습니다:

```jldoctest helloworldstring
julia> str[4:9]
"lo, wo"
```

`str[k]`와 `str[k:k]` 표현식이 동일한 결과를 주지 않는다는 점에 유의하세요:

```jldoctest helloworldstring
julia> str[6]
',': ASCII/Unicode U+002C (category Po: Punctuation, other)

julia> str[6:6]
","
```

전자는 `Char` 유형의 단일 문자 값인 반면, 후자는 단일 문자만 포함하는 문자열 값입니다. 줄리아에서는 이 두 가지가 매우 다릅니다.

범위 인덱싱은 원래 문자열의 선택된 부분을 복사합니다. 또는 [`SubString`](@ref) 유형을 사용하여 문자열에 대한 뷰를 생성할 수 있습니다. 더 간단하게, 코드 블록에서 [`@views`](@ref) 매크로를 사용하면 모든 문자열 슬라이스가 서브스트링으로 변환됩니다. 예를 들어:

```jldoctest
julia> str = "long string"
"long string"

julia> substr = SubString(str, 1, 4)
"long"

julia> typeof(substr)
SubString{String}

julia> @views typeof(str[1:4]) # @views converts slices to SubStrings
SubString{String}
```

여러 표준 함수는 [`chop`](@ref), [`chomp`](@ref) 또는 [`strip`](@ref)와 같은 값을 반환합니다. 이들은 [`SubString`](@ref)를 반환합니다.

## Unicode and UTF-8

Julia는 유니코드 문자와 문자열을 완전히 지원합니다. [discussed above](@ref man-characters)와 같이, 문자 리터럴에서 유니코드 코드 포인트는 유니코드 `\u` 및 `\U` 이스케이프 시퀀스를 사용하여 표현할 수 있으며, 모든 표준 C 이스케이프 시퀀스도 사용할 수 있습니다. 이러한 방법은 문자열 리터럴을 작성하는 데에도 사용할 수 있습니다:

```jldoctest unicodestring
julia> s = "\u2200 x \u2203 y"
"∀ x ∃ y"
```

이러한 유니코드 문자가 이스케이프 형식으로 표시되거나 특수 문자로 표시되는 것은 터미널의 로케일 설정 및 유니코드 지원에 따라 다릅니다. 문자열 리터럴은 UTF-8 인코딩을 사용하여 인코딩됩니다. UTF-8은 가변 길이 인코딩으로, 모든 문자가 동일한 바이트 수("코드 유닛")로 인코딩되지 않음을 의미합니다. UTF-8에서 ASCII 문자는 즉, 코드 포인트가 0x80(128) 미만인 문자는 ASCII에서와 같이 단일 바이트를 사용하여 인코딩되며, 코드 포인트 0x80 이상은 여러 바이트를 사용하여 인코딩됩니다 — 문자당 최대 네 개까지.

줄리아의 문자열 인덱스는 코드 유닛(UTF-8의 경우 바이트)을 참조하며, 이는 임의의 문자를 인코딩하는 데 사용되는 고정 너비의 빌딩 블록입니다(코드 포인트). 이는 `String`의 모든 인덱스가 반드시 문자에 대한 유효한 인덱스가 아닐 수 있음을 의미합니다. 유효하지 않은 바이트 인덱스에서 문자열에 인덱싱하면 오류가 발생합니다:

```jldoctest unicodestring
julia> s[1]
'∀': Unicode U+2200 (category Sm: Symbol, math)

julia> s[2]
ERROR: StringIndexError: invalid index [2], valid nearby indices [1]=>'∀', [4]=>' '
Stacktrace:
[...]

julia> s[3]
ERROR: StringIndexError: invalid index [3], valid nearby indices [1]=>'∀', [4]=>' '
Stacktrace:
[...]

julia> s[4]
' ': ASCII/Unicode U+0020 (category Zs: Separator, space)
```

이 경우, 문자 `∀`는 3바이트 문자이므로 인덱스 2와 3은 유효하지 않으며 다음 문자의 인덱스는 4입니다. 이 다음 유효한 인덱스는 [`nextind(s,1)`](@ref)로 계산할 수 있으며, 그 다음 인덱스는 `nextind(s,4)`로 계산할 수 있습니다.

`end`는 항상 컬렉션의 마지막 유효한 인덱스이므로, `end-1`은 마지막에서 두 번째 문자가 다중 바이트인 경우 유효하지 않은 바이트 인덱스를 참조합니다.

```jldoctest unicodestring
julia> s[end-1]
' ': ASCII/Unicode U+0020 (category Zs: Separator, space)

julia> s[end-2]
ERROR: StringIndexError: invalid index [9], valid nearby indices [7]=>'∃', [10]=>' '
Stacktrace:
[...]

julia> s[prevind(s, end, 2)]
'∃': Unicode U+2203 (category Sm: Symbol, math)
```

첫 번째 경우는 작동합니다. 마지막 문자 `y`와 공백은 각각 1바이트 문자이고, 반면 `end-2`는 `∃` 다바이트 표현의 중간을 가리킵니다. 이 경우에 대한 올바른 방법은 `prevind(s, lastindex(s), 2)`를 사용하는 것이며, 만약 그 값을 사용하여 `s`에 인덱싱하려면 `s[prevind(s, end, 2)]`라고 쓸 수 있고 `end`는 `lastindex(s)`로 확장됩니다.

부분 문자열을 범위 인덱싱을 사용하여 추출할 때 유효한 바이트 인덱스가 필요하며, 그렇지 않으면 오류가 발생합니다:

```jldoctest unicodestring
julia> s[1:1]
"∀"

julia> s[1:2]
ERROR: StringIndexError: invalid index [2], valid nearby indices [1]=>'∀', [4]=>' '
Stacktrace:
[...]

julia> s[1:4]
"∀ "
```

변수 길이 인코딩 때문에, 문자열의 문자 수([`length(s)`](@ref))는 항상 마지막 인덱스와 같지 않습니다. 인덱스 1부터 [`lastindex(s)`](@ref)까지 반복하면서 `s`에 인덱싱하면, 오류가 발생하지 않을 때 반환되는 문자 시퀀스는 문자열 `s`를 구성하는 문자 시퀀스입니다. 따라서 `length(s) <= lastindex(s)`입니다. 문자열의 각 문자는 고유한 인덱스를 가져야 하기 때문입니다. 다음은 `s`의 문자를 반복하는 비효율적이고 장황한 방법입니다:

```jldoctest unicodestring
julia> for i = firstindex(s):lastindex(s)
           try
               println(s[i])
           catch
               # ignore the index error
           end
       end
∀

x

∃

y
```

빈 줄에는 실제로 공백이 있습니다. 다행히도, 위의 어색한 관용구는 문자열의 문자를 반복하는 데 필요하지 않습니다. 문자열을 반복 가능한 객체로 사용할 수 있으므로 예외 처리가 필요하지 않습니다:

```jldoctest unicodestring
julia> for c in s
           println(c)
       end
∀

x

∃

y
```

문자열에 대한 유효한 인덱스를 얻어야 하는 경우, 위에서 언급한 대로 [`nextind`](@ref) 및 [`prevind`](@ref) 함수를 사용하여 다음/이전 유효 인덱스로 증가/감소할 수 있습니다. 또한 [`eachindex`](@ref) 함수를 사용하여 유효한 문자 인덱스를 반복할 수 있습니다:

```jldoctest unicodestring
julia> collect(eachindex(s))
7-element Vector{Int64}:
  1
  4
  5
  6
  7
 10
 11
```

인코딩의 원시 코드 단위(UTF-8의 바이트)에 접근하려면 [`codeunit(s,i)`](@ref) 함수를 사용할 수 있습니다. 여기서 인덱스 `i`는 `1`부터 [`ncodeunits(s)`](@ref)까지 연속적으로 실행됩니다. [`codeunits(s)`](@ref) 함수는 이러한 원시 코드 단위(바이트)에 배열로 접근할 수 있는 `AbstractVector{UInt8}` 래퍼를 반환합니다.

줄리아의 문자열은 유효하지 않은 UTF-8 코드 유닛 시퀀스를 포함할 수 있습니다. 이 규칙은 모든 바이트 시퀀스를 `String`으로 취급할 수 있게 합니다. 이러한 상황에서 규칙은 왼쪽에서 오른쪽으로 코드 유닛 시퀀스를 구문 분석할 때, 다음 비트 패턴 중 하나의 시작과 일치하는 가장 긴 8비트 코드 유닛 시퀀스에 의해 문자가 형성된다는 것입니다 (각 `x`는 `0` 또는 `1`일 수 있습니다):

  * `0xxxxxxx`;
  * `110xxxxx` `10xxxxxx`;
  * `1110xxxx` `10xxxxxx` `10xxxxxx`;
  * `11110xxx` `10xxxxxx` `10xxxxxx` `10xxxxxx`;
  * `10xxxxxx`;
  * `11111xxx`.

특히 이것은 너무 긴 코드 유닛 시퀀스와 그 접두사가 여러 개의 잘못된 문자로 처리되는 것이 아니라 단일 잘못된 문자로 처리된다는 것을 의미합니다. 이 규칙은 예를 들어 설명하는 것이 가장 좋습니다:

```julia-repl
julia> s = "\xc0\xa0\xe2\x88\xe2|"
"\xc0\xa0\xe2\x88\xe2|"

julia> foreach(display, s)
'\xc0\xa0': [overlong] ASCII/Unicode U+0020 (category Zs: Separator, space)
'\xe2\x88': Malformed UTF-8 (category Ma: Malformed, bad data)
'\xe2': Malformed UTF-8 (category Ma: Malformed, bad data)
'|': ASCII/Unicode U+007C (category Sm: Symbol, math)

julia> isvalid.(collect(s))
4-element BitArray{1}:
 0
 0
 0
 1

julia> s2 = "\xf7\xbf\xbf\xbf"
"\U1fffff"

julia> foreach(display, s2)
'\U1fffff': Unicode U+1FFFFF (category In: Invalid, too high)
```

문자열 `s`의 첫 번째 두 코드 유닛이 공백 문자의 오버롱 인코딩을 형성하는 것을 볼 수 있습니다. 이는 유효하지 않지만 문자열에서 단일 문자로 허용됩니다. 다음 두 코드 유닛은 세 바이트 UTF-8 시퀀스의 유효한 시작을 형성합니다. 그러나 다섯 번째 코드 유닛 `\xe2`는 그 유효한 연속성이 아닙니다. 따라서 코드 유닛 3과 4도 이 문자열에서 잘못된 문자로 해석됩니다. 마찬가지로 코드 유닛 5는 `|`가 그에 대한 유효한 연속성이 아니기 때문에 잘못된 문자를 형성합니다. 마지막으로 문자열 `s2`는 하나의 너무 높은 코드 포인트를 포함하고 있습니다.

줄리아는 기본적으로 UTF-8 인코딩을 사용하며, 새로운 인코딩에 대한 지원은 패키지를 통해 추가할 수 있습니다. 예를 들어, [LegacyStrings.jl](https://github.com/JuliaStrings/LegacyStrings.jl) 패키지는 `UTF16String` 및 `UTF32String` 타입을 구현합니다. 다른 인코딩에 대한 추가 논의와 이를 지원하는 방법은 현재 이 문서의 범위를 벗어납니다. UTF-8 인코딩 문제에 대한 추가 논의는 아래의 [byte array literals](@ref man-byte-array-literals) 섹션을 참조하십시오. [`transcode`](@ref) 함수는 다양한 UTF-xx 인코딩 간에 데이터를 변환하는 데 제공되며, 주로 외부 데이터 및 라이브러리와 작업할 때 사용됩니다.

## [Concatenation](@id man-concatenation)

가장 일반적이고 유용한 문자열 작업 중 하나는 연결입니다:

```jldoctest stringconcat
julia> greet = "Hello"
"Hello"

julia> whom = "world"
"world"

julia> string(greet, ", ", whom, ".\n")
"Hello, world.\n"
```

잠재적으로 위험한 상황, 예를 들어 유효하지 않은 UTF-8 문자열의 연결에 대해 인식하는 것이 중요합니다. 결과 문자열은 입력 문자열과 다른 문자를 포함할 수 있으며, 그 문자 수는 연결된 문자열의 문자 수의 합보다 적을 수 있습니다. 예를 들어:

```julia-repl
julia> a, b = "\xe2\x88", "\x80"
("\xe2\x88", "\x80")

julia> c = string(a, b)
"∀"

julia> collect.([a, b, c])
3-element Vector{Vector{Char}}:
 ['\xe2\x88']
 ['\x80']
 ['∀']

julia> length.([a, b, c])
3-element Vector{Int64}:
 1
 1
 1
```

이 상황은 유효하지 않은 UTF-8 문자열에만 발생할 수 있습니다. 유효한 UTF-8 문자열의 경우, 연결은 문자열의 모든 문자를 보존하고 문자열 길이의 가산성을 유지합니다.

줄리아는 문자열 연결을 위해 [`*`](@ref)도 제공합니다:

```jldoctest stringconcat
julia> greet * ", " * whom * ".\n"
"Hello, world.\n"
```

`*`는 문자열 연결을 위해 `+`를 제공하는 언어의 사용자에게는 놀라운 선택처럼 보일 수 있지만, `*`의 이러한 사용은 수학, 특히 추상 대수학에서 선례가 있습니다.

수학에서 `+`는 일반적으로 피연산자의 순서가 중요하지 않은 *가환* 연산을 나타냅니다. 이의 예로는 행렬 덧셈이 있으며, 여기서 `A + B == B + A`는 동일한 형태를 가진 모든 행렬 `A`와 `B`에 대해 성립합니다. 반대로, `*`는 일반적으로 피연산자의 순서가 중요한 *비가환* 연산을 나타냅니다. 이의 예로는 행렬 곱셈이 있으며, 일반적으로 `A * B != B * A`입니다. 행렬 곱셈과 마찬가지로, 문자열 연결도 비가환적입니다: `greet * whom != whom * greet`. 따라서 `*`는 일반적인 수학적 사용과 일치하는 중위 문자열 연결 연산자로 더 자연스러운 선택입니다.

보다 정확하게, 모든 유한 길이 문자열의 집합 *S*와 문자열 연결 연산자 `*`는 [free monoid](https://en.wikipedia.org/wiki/Free_monoid) (*S*, `*`)를 형성합니다. 이 집합의 항등원은 빈 문자열 `""`입니다. 자유 모노이드가 비가환일 때, 연산은 일반적으로 `+`가 아닌 `\cdot`, `*` 또는 유사한 기호로 표현됩니다. `+`는 일반적으로 가환성을 의미합니다.

## [Interpolation](@id string-interpolation)

문자열을 연결하여 구성하는 것은 다소 번거로울 수 있습니다. 이러한 장황한 호출인 [`string`](@ref) 또는 반복적인 곱셈의 필요성을 줄이기 위해, Julia는 Perl처럼 `$`를 사용하여 문자열 리터럴에 보간을 허용합니다:

```jldoctest
julia> greet = "Hello"; whom = "world";

julia> "$greet, $whom.\n"
"Hello, world.\n"
```

이것은 더 읽기 쉽고 편리하며 위의 문자열 연결과 동등합니다. 시스템은 이 명백한 단일 문자열 리터럴을 호출 `string(greet, ", ", whom, ".\n")`로 재작성합니다.

`$` 다음의 가장 짧은 완전 표현식은 문자열에 삽입될 값으로 간주됩니다. 따라서 괄호를 사용하여 문자열에 어떤 표현식이든 삽입할 수 있습니다:

```jldoctest
julia> "1 + 2 = $(1 + 2)"
"1 + 2 = 3"
```

둘 다 연결(concatenation)과 문자열 보간(string interpolation)은 [`string`](@ref)를 호출하여 객체를 문자열 형태로 변환합니다. 그러나 `string`은 실제로 [`print`](@ref)의 출력을 반환하므로, 새로운 타입은 `4d61726b646f776e2e436f64652822222c20227072696e742229_40726566` 또는 [`show`](@ref)에 메서드를 추가해야 합니다.

대부분의 비-`AbstractString` 객체는 리터럴 표현으로 입력된 방식과 밀접하게 일치하는 문자열로 변환됩니다:

```jldoctest
julia> v = [1,2,3]
3-element Vector{Int64}:
 1
 2
 3

julia> "v: $v"
"v: [1, 2, 3]"
```

[`string`](@ref)는 `AbstractString` 및 `AbstractChar` 값의 식별자이므로, 이들은 문자열에 인용부호 없이 이스케이프 없이 그대로 삽입됩니다:

```jldoctest
julia> c = 'x'
'x': ASCII/Unicode U+0078 (category Ll: Letter, lowercase)

julia> "hi, $c"
"hi, x"
```

문자열 리터럴에 리터럴 `$`를 포함하려면, 백슬래시로 이스케이프하세요:

```jldoctest
julia> print("I have \$100 in my account.\n")
I have $100 in my account.
```

## Triple-Quoted String Literals

삼중 따옴표(`"""..."""`)를 사용하여 문자열을 생성할 때, 긴 텍스트 블록을 생성하는 데 유용한 특별한 동작이 있습니다.

먼저, 삼중 따옴표 문자열은 가장 덜 들여쓰기된 줄의 수준으로 들여쓰기가 제거됩니다. 이는 들여쓰기가 있는 코드 내에서 문자열을 정의하는 데 유용합니다. 예를 들어:

```jldoctest
julia> str = """
           Hello,
           world.
         """
"  Hello,\n  world.\n"
```

이 경우 닫는 `"""` 이전의 마지막 (빈) 줄이 들여쓰기 수준을 설정합니다.

들여쓰기 수준은 모든 줄에서 공백 또는 탭의 가장 긴 공통 시작 시퀀스로 결정되며, 여는 `"""` 다음의 줄과 공백 또는 탭만 포함된 줄은 제외됩니다(닫는 `"""`가 포함된 줄은 항상 포함됨). 그런 다음 여는 `"""` 다음의 텍스트를 제외한 모든 줄에서 공통 시작 시퀀스가 제거됩니다(이 시퀀스로 시작하는 공백 및 탭만 포함된 줄도 포함됨), 예:

```jldoctest
julia> """    This
         is
           a test"""
"    This\nis\n  a test"
```

다음으로, 열기 `"""` 다음에 줄 바꿈이 오면, 줄 바꿈은 결과 문자열에서 제거됩니다.

```julia
"""hello"""
```

에 해당합니다

```julia
"""
hello"""
```

하지만

```julia
"""

hello"""
```

will contain a literal newline at the beginning.

줄 바꿈 제거는 들여쓰기를 제거한 후에 수행됩니다. 예를 들어:

```jldoctest
julia> """
         Hello,
         world."""
"Hello,\nworld."
```

줄 바꿈이 백슬래시를 사용하여 제거되면, 들여쓰기도 존중됩니다:

```jldoctest
julia> """
         Averylong\
         word"""
"Averylongword"
```

후행 공백은 변경되지 않습니다.

삼중 따옴표 문자열 리터럴은 이스케이프 없이 `"` 문자를 포함할 수 있습니다.

문자열에서 줄 바꿈은 단일 또는 삼중 따옴표로 묶인 경우에도 문자열에 새 줄(LF) 문자 `\n`을 생성합니다. 편집기가 줄 끝에 캐리지 리턴 `\r`(CR) 또는 CRLF 조합을 사용하더라도 마찬가지입니다. 문자열에 CR을 포함하려면 명시적인 이스케이프 `\r`을 사용하십시오. 예를 들어, 리터럴 문자열 `"a CRLF line ending\r\n"`을 입력할 수 있습니다.

## Common Operations

문자열을 표준 비교 연산자를 사용하여 사전식으로 비교할 수 있습니다:

```jldoctest
julia> "abracadabra" < "xylophone"
true

julia> "abracadabra" == "xylophone"
false

julia> "Hello, world." != "Goodbye, world."
true

julia> "1 + 2 = 3" == "1 + 2 = $(1 + 2)"
true
```

특정 문자의 인덱스를 검색하려면 [`findfirst`](@ref) 및 [`findlast`](@ref) 함수를 사용할 수 있습니다:

```jldoctest
julia> findfirst('o', "xylophone")
4

julia> findlast('o', "xylophone")
7

julia> findfirst('z', "xylophone")
```

주어진 오프셋에서 문자를 검색하려면 [`findnext`](@ref) 및 [`findprev`](@ref) 함수를 사용할 수 있습니다:

```jldoctest
julia> findnext('o', "xylophone", 1)
4

julia> findnext('o', "xylophone", 5)
7

julia> findprev('o', "xylophone", 5)
4

julia> findnext('o', "xylophone", 8)
```

[`occursin`](@ref) 함수를 사용하여 문자열 내에 부분 문자열이 있는지 확인할 수 있습니다:

```jldoctest
julia> occursin("world", "Hello, world.")
true

julia> occursin("o", "Xylophon")
true

julia> occursin("a", "Xylophon")
false

julia> occursin('o', "Xylophon")
true
```

마지막 예제는 [`occursin`](@ref)가 문자 리터럴을 찾을 수도 있음을 보여줍니다.

두 개의 유용한 문자열 함수는 [`repeat`](@ref)와 [`join`](@ref)입니다:

```jldoctest
julia> repeat(".:Z:.", 10)
".:Z:..:Z:..:Z:..:Z:..:Z:..:Z:..:Z:..:Z:..:Z:..:Z:."

julia> join(["apples", "bananas", "pineapples"], ", ", " and ")
"apples, bananas and pineapples"
```

다른 유용한 기능으로는:

  * [`firstindex(str)`](@ref)는 `str`에 인덱싱하는 데 사용할 수 있는 최소 (바이트) 인덱스를 제공합니다 (문자열의 경우 항상 1, 다른 컨테이너의 경우 반드시 그렇지는 않음).
  * [`lastindex(str)`](@ref)는 `str`에 인덱싱할 수 있는 최대 (바이트) 인덱스를 제공합니다.
  * [`length(str)`](@ref)의 `str`에서 문자 수는 64입니다.
  * [`length(str, i, j)`](@ref)에서 `i`부터 `j`까지의 `str`에서 유효한 문자 인덱스의 수.
  * [`ncodeunits(str)`](@ref) 숫자 [code units](https://en.wikipedia.org/wiki/Character_encoding#Terminology) 문자열에서.
  * [`codeunit(str, i)`](@ref)는 문자열 `str`에서 인덱스 `i`의 코드 유닛 값을 제공합니다.
  * [`thisind(str, i)`](@ref) given an arbitrary index into a string find the first index of the character into which the index points.
  * [`nextind(str, i, n=1)`](@ref) n번째 문자의 시작을 인덱스 `i` 이후에서 찾으세요.
  * [`prevind(str, i, n=1)`](@ref) n번째 문자의 시작을 인덱스 `i` 이전에서 찾으세요.

## [Non-Standard String Literals](@id non-standard-string-literals)

문자열을 구성하거나 문자열 의미를 사용하고 싶지만 표준 문자열 구성의 동작이 필요에 맞지 않는 상황이 있습니다. 이러한 종류의 상황을 위해 Julia는 비표준 문자열 리터럴을 제공합니다. 비표준 문자열 리터럴은 일반적인 큰따옴표로 묶인 문자열 리터럴처럼 보이지만, 식별자로 즉시 접두사가 붙으며, 일반 문자열 리터럴과는 다르게 동작할 수 있습니다.

[Regular expressions](@ref man-regex-literals), [byte array literals](@ref man-byte-array-literals), 및 [version number literals](@ref man-version-number-literals)는 아래에 설명된 바와 같이 비표준 문자열 리터럴의 몇 가지 예입니다. 사용자와 패키지도 새로운 비표준 문자열 리터럴을 정의할 수 있습니다. 추가 문서는 [Metaprogramming](@ref meta-non-standard-string-literals) 섹션에 제공됩니다.

## [Regular Expressions](@id man-regex-literals)

때때로 당신은 정확한 문자열을 찾고 있는 것이 아니라 특정 *패턴*을 찾고 있습니다. 예를 들어, 큰 텍스트 파일에서 단일 날짜를 추출하려고 한다고 가정해 보겠습니다. 그 날짜가 무엇인지 모르지만(그래서 당신은 그것을 찾고 있는 것입니다), 그 날짜는 `YYYY-MM-DD`와 비슷한 형식일 것이라는 것을 알고 있습니다. 정규 표현식은 이러한 패턴을 지정하고 검색할 수 있게 해줍니다.

줄리아는 [PCRE](https://www.pcre.org/) 라이브러리에서 제공하는 Perl 호환 정규 표현식(정규식) 버전 2를 사용합니다(자세한 내용은 [PCRE2 syntax description](https://www.pcre.org/current/doc/html/pcre2syntax.html)를 참조하십시오). 정규 표현식은 문자열과 두 가지 방식으로 관련이 있습니다: 명백한 연결은 정규 표현식이 문자열에서 정규 패턴을 찾는 데 사용된다는 것입니다; 다른 연결은 정규 표현식이 문자열로 입력되어 상태 기계로 구문 분석되어 문자열에서 패턴을 효율적으로 검색하는 데 사용된다는 것입니다. 줄리아에서 정규 표현식은 `r`로 시작하는 다양한 식별자로 접두사가 붙은 비표준 문자열 리터럴을 사용하여 입력됩니다. 옵션이 켜지지 않은 가장 기본적인 정규 표현식 리터럴은 단순히 `r"..."`를 사용합니다:

```jldoctest
julia> re = r"^\s*(?:#|$)"
r"^\s*(?:#|$)"

julia> typeof(re)
Regex
```

정규 표현식이 문자열과 일치하는지 확인하려면 [`occursin`](@ref)를 사용하세요:

```jldoctest
julia> occursin(r"^\s*(?:#|$)", "not a comment")
false

julia> occursin(r"^\s*(?:#|$)", "# a comment")
true
```

여기에서 볼 수 있듯이, [`occursin`](@ref)는 주어진 정규 표현식이 문자열에서 일치하는지 여부를 나타내는 true 또는 false를 반환합니다. 그러나 일반적으로 문자열이 일치하는지 여부뿐만 아니라 *어떻게* 일치하는지도 알고 싶어합니다. 일치에 대한 이 정보를 캡처하려면 대신 [`match`](@ref) 함수를 사용하세요:

```jldoctest
julia> match(r"^\s*(?:#|$)", "not a comment")

julia> match(r"^\s*(?:#|$)", "# a comment")
RegexMatch("#")
```

주어진 문자열과 정규 표현식이 일치하지 않으면, [`match`](@ref)는 [`nothing`](@ref)를 반환합니다. 이는 대화형 프롬프트에서 아무것도 출력하지 않는 특별한 값입니다. 출력하지 않는 것 외에는 완전히 정상적인 값이며, 프로그래밍적으로 테스트할 수 있습니다:

```julia
m = match(r"^\s*(?:#|$)", line)
if m === nothing
    println("not a comment")
else
    println("blank or comment")
end
```

정규 표현식이 일치하는 경우, [`match`](@ref)가 반환하는 값은 [`RegexMatch`](@ref) 객체입니다. 이러한 객체는 표현식이 어떻게 일치하는지를 기록하며, 패턴이 일치하는 부분 문자열과 캡처된 부분 문자열(있는 경우)을 포함합니다. 이 예제는 일치하는 부분 문자열의 일부만 캡처하지만, 아마도 우리는 주석 문자 뒤에 있는 비어 있지 않은 텍스트를 캡처하고 싶을 것입니다. 우리는 다음과 같이 할 수 있습니다:

```jldoctest
julia> m = match(r"^\s*(?:#\s*(.*?)\s*$)", "# a comment ")
RegexMatch("# a comment ", 1="a comment")
```

[`match`](@ref)를 호출할 때, 검색을 시작할 인덱스를 지정할 수 있는 옵션이 있습니다. 예를 들어:

```jldoctest
julia> m = match(r"[0-9]","aaaa1aaaa2aaaa3",1)
RegexMatch("1")

julia> m = match(r"[0-9]","aaaa1aaaa2aaaa3",6)
RegexMatch("2")

julia> m = match(r"[0-9]","aaaa1aaaa2aaaa3",11)
RegexMatch("3")
```

`RegexMatch` 객체에서 다음 정보를 추출할 수 있습니다:

  * 전체 하위 문자열 일치: `m.match`
  * 캡처된 하위 문자열을 문자열 배열로: `m.captures`
  * 전체 매치가 시작되는 오프셋: `m.offset`
  * 캡처된 서브스트링의 오프셋을 벡터로 나타낸 것: `m.offsets`

캡처가 일치하지 않을 경우, 부분 문자열 대신 `m.captures`는 해당 위치에 `nothing`을 포함하고, `m.offsets`는 0 오프셋을 가집니다 (줄리아에서 인덱스는 1 기반이므로 문자열에 대한 0 오프셋은 유효하지 않습니다). 다음은 다소 억지스러운 예제 쌍입니다:

```jldoctest acdmatch
julia> m = match(r"(a|b)(c)?(d)", "acd")
RegexMatch("acd", 1="a", 2="c", 3="d")

julia> m.match
"acd"

julia> m.captures
3-element Vector{Union{Nothing, SubString{String}}}:
 "a"
 "c"
 "d"

julia> m.offset
1

julia> m.offsets
3-element Vector{Int64}:
 1
 2
 3

julia> m = match(r"(a|b)(c)?(d)", "ad")
RegexMatch("ad", 1="a", 2=nothing, 3="d")

julia> m.match
"ad"

julia> m.captures
3-element Vector{Union{Nothing, SubString{String}}}:
 "a"
 nothing
 "d"

julia> m.offset
1

julia> m.offsets
3-element Vector{Int64}:
 1
 0
 2
```

캡처가 배열로 반환되면 구조 분해 구문을 사용하여 로컬 변수에 바인딩할 수 있어 편리합니다. 편의상, `RegexMatch` 객체는 `captures` 필드를 통해 전달되는 반복자 메서드를 구현하므로, 매치 객체를 직접 구조 분해할 수 있습니다:

```jldoctest acdmatch
julia> first, second, third = m; first
"a"
```

캡처는 캡처 그룹의 번호나 이름으로 `RegexMatch` 객체를 인덱싱하여 접근할 수도 있습니다:

```jldoctest
julia> m=match(r"(?<hour>\d+):(?<minute>\d+)","12:45")
RegexMatch("12:45", hour="12", minute="45")

julia> m[:minute]
"45"

julia> m[2]
"45"
```

캡처는 [`replace`](@ref)를 사용할 때 치환 문자열에서 참조할 수 있으며, `\n`을 사용하여 n번째 캡처 그룹을 참조하고 치환 문자열을 `s`로 접두어를 붙입니다. 캡처 그룹 0은 전체 일치 객체를 참조합니다. 명명된 캡처 그룹은 치환에서 `\g<groupname>`으로 참조할 수 있습니다. 예를 들어:

```jldoctest
julia> replace("first second", r"(\w+) (?<agroup>\w+)" => s"\g<agroup> \1")
"second first"
```

번호가 매겨진 캡처 그룹은 `\g<n>`로 참조할 수 있으며, 이는 다음과 같이 모호성을 해소합니다:

```jldoctest
julia> replace("a", r"." => s"\g<0>1")
"a1"
```

정규 표현식의 동작은 닫는 큰따옴표 뒤에 `i`, `m`, `s`, `x` 플래그의 조합을 사용하여 수정할 수 있습니다. 이 플래그는 Perl에서와 동일한 의미를 가지며, [perlre manpage](https://perldoc.perl.org/perlre#Modifiers)의 발췌문에서 설명되어 있습니다.

```
i   Do case-insensitive pattern matching.

    If locale matching rules are in effect, the case map is taken
    from the current locale for code points less than 255, and
    from Unicode rules for larger code points. However, matches
    that would cross the Unicode rules/non-Unicode rules boundary
    (ords 255/256) will not succeed.

m   Treat string as multiple lines.  That is, change "^" and "$"
    from matching the start or end of the string to matching the
    start or end of any line anywhere within the string.

s   Treat string as single line.  That is, change "." to match any
    character whatsoever, even a newline, which normally it would
    not match.

    Used together, as r""ms, they let the "." match any character
    whatsoever, while still allowing "^" and "$" to match,
    respectively, just after and just before newlines within the
    string.

x   Tells the regular expression parser to ignore most whitespace
    that is neither backslashed nor within a character class. You
    can use this to break up your regular expression into
    (slightly) more readable parts. The '#' character is also
    treated as a metacharacter introducing a comment, just as in
    ordinary code.
```

예를 들어, 다음 정규 표현식은 세 가지 플래그가 모두 켜져 있습니다:

```jldoctest
julia> r"a+.*b+.*d$"ism
r"a+.*b+.*d$"ims

julia> match(r"a+.*b+.*d$"ism, "Goodbye,\nOh, angry,\nBad world\n")
RegexMatch("angry,\nBad world")
```

`r"..."` 리터럴은 보간 및 이스케이프 없이 구성됩니다(따옴표 `"`는 여전히 이스케이프해야 함). 다음은 표준 문자열 리터럴과의 차이를 보여주는 예입니다:

```julia-repl
julia> x = 10
10

julia> r"$x"
r"$x"

julia> "$x"
"10"

julia> r"\x"
r"\x"

julia> "\x"
ERROR: syntax: invalid escape sequence
```

세 개의 따옴표로 묶인 정규 표현식 문자열, 형식 `r"""..."""`,도 지원되며(따옴표나 줄 바꿈이 포함된 정규 표현식에 편리할 수 있습니다).

`Regex()` 생성자는 유효한 정규 표현식 문자열을 프로그래밍 방식으로 생성하는 데 사용될 수 있습니다. 이를 통해 정규 표현식 문자열을 구성할 때 문자열 변수의 내용과 기타 문자열 작업을 사용할 수 있습니다. 위의 정규 표현식 코드 중 어떤 것도 `Regex()`의 단일 문자열 인수 내에서 사용할 수 있습니다. 다음은 몇 가지 예입니다:

```jldoctest
julia> using Dates

julia> d = Date(1962,7,10)
1962-07-10

julia> regex_d = Regex("Day " * string(day(d)))
r"Day 10"

julia> match(regex_d, "It happened on Day 10")
RegexMatch("Day 10")

julia> name = "Jon"
"Jon"

julia> regex_name = Regex("[\"( ]\\Q$name\\E[\") ]")  # interpolate value of name
r"[\"( ]\QJon\E[\") ]"

julia> match(regex_name, " Jon ")
RegexMatch(" Jon ")

julia> match(regex_name, "[Jon]") === nothing
true
```

`\Q...\E` 이스케이프 시퀀스의 사용에 유의하세요. `\Q`와 `\E` 사이의 모든 문자는 리터럴 문자로 해석됩니다. 이는 그렇지 않으면 정규 표현식 메타문자가 될 문자를 일치시키는 데 편리합니다. 그러나 이 기능을 문자열 보간과 함께 사용할 때는 주의가 필요합니다. 보간된 문자열 자체에 `\E` 시퀀스가 포함될 수 있어 리터럴 일치를 예기치 않게 종료할 수 있습니다. 사용자 입력은 정규 표현식에 포함되기 전에 정리되어야 합니다.

## [Byte Array Literals](@id man-byte-array-literals)

또 다른 유용한 비표준 문자열 리터럴은 바이트 배열 문자열 리터럴: `b"..."`입니다. 이 형식은 문자열 표기를 사용하여 읽기 전용 리터럴 바이트 배열을 표현할 수 있게 해줍니다. 즉, [`UInt8`](@ref) 값의 배열입니다. 이러한 객체의 유형은 `CodeUnits{UInt8, String}`입니다. 바이트 배열 리터럴에 대한 규칙은 다음과 같습니다:

  * ASCII 문자와 ASCII 이스케이프는 단일 바이트를 생성합니다.
  * `\x` 및 8진수 이스케이프 시퀀스는 이스케이프 값에 해당하는 *바이트*를 생성합니다.
  * 유니코드 이스케이프 시퀀스는 해당 코드 포인트를 UTF-8로 인코딩하는 바이트 시퀀스를 생성합니다.

이 규칙들 사이에는 일부 중복이 있습니다. `\x`의 동작과 0x80(128) 미만의 8진수 이스케이프는 처음 두 규칙 모두에 의해 다루어지지만, 여기서 이 규칙들은 일치합니다. 함께, 이 규칙들은 ASCII 문자, 임의의 바이트 값 및 UTF-8 시퀀스를 쉽게 사용하여 바이트 배열을 생성할 수 있게 해줍니다. 다음은 세 가지를 모두 사용하는 예입니다:

```jldoctest
julia> b"DATA\xff\u2200"
8-element Base.CodeUnits{UInt8, String}:
 0x44
 0x41
 0x54
 0x41
 0xff
 0xe2
 0x88
 0x80
```

ASCII 문자열 "DATA"는 바이트 68, 65, 84, 65에 해당합니다. `\xff`는 단일 바이트 255를 생성합니다. 유니코드 이스케이프 `\u2200`는 UTF-8로 인코딩될 때 세 바이트 226, 136, 128로 인코딩됩니다. 결과 바이트 배열이 유효한 UTF-8 문자열에 해당하지 않음을 주의하세요:

```jldoctest
julia> isvalid("DATA\xff\u2200")
false
```

`CodeUnits{UInt8, String}` 타입은 읽기 전용 `UInt8` 배열처럼 동작하며, 표준 벡터가 필요하면 `Vector{UInt8}`를 사용하여 변환할 수 있습니다:

```jldoctest
julia> x = b"123"
3-element Base.CodeUnits{UInt8, String}:
 0x31
 0x32
 0x33

julia> x[1]
0x31

julia> x[1] = 0x32
ERROR: CanonicalIndexError: setindex! not defined for Base.CodeUnits{UInt8, String}
[...]

julia> Vector{UInt8}(x)
3-element Vector{UInt8}:
 0x31
 0x32
 0x33
```

또한 `\xff`와 `\uff` 사이의 중요한 차이를 관찰하십시오: 전자는 *바이트 255*를 인코딩하는 이스케이프 시퀀스인 반면, 후자는 *코드 포인트 255*를 나타내며, 이는 UTF-8에서 두 바이트로 인코딩됩니다:

```jldoctest
julia> b"\xff"
1-element Base.CodeUnits{UInt8, String}:
 0xff

julia> b"\uff"
2-element Base.CodeUnits{UInt8, String}:
 0xc3
 0xbf
```

문자 리터럴은 동일한 동작을 사용합니다.

코드 포인트가 `\u80`보다 작은 경우, 각 코드 포인트의 UTF-8 인코딩은 해당 `\x` 이스케이프에 의해 생성된 단일 바이트와 동일하므로, 이 구분은 안전하게 무시할 수 있습니다. 그러나 `\x80`에서 `\xff`까지의 이스케이프와 `\u80`에서 `\uff`까지의 이스케이프 간에는 큰 차이가 있습니다. 전자의 이스케이프는 모두 단일 바이트를 인코딩하며, 이는 매우 특정한 연속 바이트가 뒤따르지 않는 한 유효한 UTF-8 데이터 형성을 하지 않습니다. 반면 후자의 이스케이프는 모두 두 바이트 인코딩으로 유니코드 코드 포인트를 나타냅니다.

이 모든 것이 매우 혼란스럽다면, ["The Absolute Minimum Every Software Developer Absolutely, Positively Must Know About Unicode and Character Sets"](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/)를 읽어보세요. 이는 유니코드와 UTF-8에 대한 훌륭한 소개이며, 이 문제에 대한 혼란을 덜어줄 수 있습니다.

## [Version Number Literals](@id man-version-number-literals)

버전 번호는 [`v"..."`](@ref @v_str) 형식의 비표준 문자열 리터럴로 쉽게 표현될 수 있습니다. 버전 번호 리터럴은 [`VersionNumber`](@ref) 객체를 생성하며, 이는 [semantic versioning](https://semver.org/)의 사양을 따릅니다. 따라서 주요, 부, 패치 숫자 값으로 구성되며, 그 뒤에 사전 릴리스 및 빌드 알파벳 주석이 옵니다. 예를 들어, `v"0.2.1-rc1+win64"`는 주요 버전 `0`, 부 버전 `2`, 패치 버전 `1`, 사전 릴리스 `rc1` 및 빌드 `win64`로 나뉩니다. 버전 리터럴을 입력할 때 주요 버전 번호를 제외한 모든 것은 선택 사항이므로, 예를 들어 `v"0.2"`는 `v"0.2.0"`(빈 사전 릴리스/빌드 주석 포함)과 동일하며, `v"2"`는 `v"2.0.0"`과 동일합니다.

`VersionNumber` 객체는 두 개 이상의 버전을 쉽게 그리고 정확하게 비교하는 데 주로 유용합니다. 예를 들어, 상수 [`VERSION`](@ref)는 `VersionNumber` 객체로서 줄리아 버전 번호를 보유하고 있으며, 따라서 간단한 문장을 사용하여 버전별 동작을 정의할 수 있습니다:

```julia
if v"0.2" <= VERSION < v"0.3-"
    # do something specific to 0.2 release series
end
```

위의 예제에서 비표준 버전 번호 `v"0.3-"`가 사용되었음을 주목하세요. 여기서 `-`가 뒤에 붙어 있습니다. 이 표기는 Julia의 표준 확장이며, `0.3` 릴리스보다 낮은 버전을 나타내는 데 사용됩니다. 즉, 모든 사전 릴리스를 포함합니다. 따라서 위의 예제에서 코드는 안정적인 `0.2` 버전에서만 실행되며, `v"0.3.0-rc1"`과 같은 버전은 제외됩니다. 불안정한 (즉, 사전 릴리스) `0.2` 버전도 허용하려면 하한 검사 조건을 다음과 같이 수정해야 합니다: `v"0.2-" <= VERSION`.

또 다른 비표준 버전 사양 확장은 후행 `+`를 사용하여 빌드 버전의 상한을 표현할 수 있게 해줍니다. 예를 들어, `VERSION > v"0.2-rc1+"`는 `0.2-rc1` 이상의 모든 버전과 해당 빌드를 의미할 수 있습니다. 이는 버전 `v"0.2-rc1+win64"`에 대해 `false`를 반환하고, `v"0.2-rc2"`에 대해 `true`를 반환합니다.

비교에서 이러한 특별한 버전을 사용하는 것은 좋은 관행입니다(특히, 상한에 대해서는 항상 후행 `-`를 사용해야 하며, 그렇지 않은 좋은 이유가 없는 한). 그러나 이들은 실제 버전 번호로 사용되어서는 안 되며, 이는 의미론적 버전 관리 체계에서 유효하지 않기 때문입니다.

[`VERSION`](@ref) 상수 외에도, `VersionNumber` 객체는 `Pkg` 모듈에서 패키지 버전과 그 의존성을 지정하는 데 널리 사용됩니다.

## [Raw String Literals](@id man-raw-string-literals)

원시 문자열은 보간이나 이스케이프 없이 `raw"..."` 형식의 비표준 문자열 리터럴로 표현할 수 있습니다. 원시 문자열 리터럴은 포함된 내용을 보간이나 이스케이프 없이 입력한 그대로 포함하는 일반 `String` 객체를 생성합니다. 이는 `$` 또는 `\`를 특수 문자로 사용하는 다른 언어의 코드나 마크업을 포함하는 문자열에 유용합니다.

예외는 따옴표가 여전히 이스케이프되어야 한다는 것입니다. 예를 들어, `raw"\""`는 `"\""`와 같습니다. 모든 문자열을 표현할 수 있도록 하려면, 백슬래시도 이스케이프되어야 하지만, 이는 오직 따옴표 문자 바로 앞에 나타날 때만 해당됩니다:

```jldoctest
julia> println(raw"\\ \\\"")
\\ \"
```

첫 번째와 두 번째 백슬래시는 출력에서 그대로 나타나며, 이는 인용 문자 앞에 있지 않기 때문입니다. 그러나 다음 백슬래시 문자는 그 뒤에 오는 백슬래시를 이스케이프하고, 마지막 백슬래시는 인용을 이스케이프합니다. 이는 이러한 백슬래시가 인용 앞에 나타나기 때문입니다.

## [Annotated Strings](@id man-annotated-strings)

!!! note
    AnnotatedStrings에 대한 API는 실험적이며 Julia 버전 간에 변경될 수 있습니다.


때때로 문자열의 영역과 관련된 메타데이터를 보유하는 것이 유용할 수 있습니다. [`AnnotatedString`](@ref Base.AnnotatedString)는 다른 문자열을 감싸고 있으며, 그 일부에 레이블이 있는 값(`:label => value`)으로 주석을 달 수 있게 해줍니다. 모든 일반 문자열 작업은 기본 문자열에 적용됩니다. 그러나 가능할 때 스타일링 정보는 보존됩니다. 이는 `4d61726b646f776e2e436f64652822222c2022416e6e6f7461746564537472696e672229_4072656620426173652e416e6e6f7461746564537472696e67`를 조작할 수 있음을 의미합니다. 부분 문자열을 가져오고, 패딩을 추가하고, 다른 문자열과 연결하는 등의 작업을 수행하면 메타데이터 주석이 함께 따라옵니다.

이 문자열 유형은 [StyledStrings stdlib](@ref stdlib-styledstrings)에 기본적이며, 스타일링 정보를 보유하기 위해 `:face`로 레이블이 지정된 주석을 사용합니다.

[`AnnotatedString`](@ref Base.AnnotatedString)를 연결할 때, 문자열 주석을 유지하려면 [`annotatedstring`](@ref Base.annotatedstring)를 사용해야 합니다. [`string`](@ref) 대신에 말이죠.

```jldoctest
julia> str = Base.AnnotatedString("hello there",
               [(1:5, :word, :greeting), (7:11, :label, 1)])
"hello there"

julia> length(str)
11

julia> lpad(str, 14)
"   hello there"

julia> typeof(lpad(str, 7))
Base.AnnotatedString{String}

julia> str2 = Base.AnnotatedString(" julia", [(2:6, :face, :magenta)])
" julia"

julia> Base.annotatedstring(str, str2)
"hello there julia"

julia> str * str2 == Base.annotatedstring(str, str2) # *-concatenation still works
true
```

[`AnnotatedString`](@ref Base.AnnotatedString)의 주석은 [`annotations`](@ref Base.annotations) 및 [`annotate!`](@ref Base.annotate!) 함수를 통해 접근하고 수정할 수 있습니다.
