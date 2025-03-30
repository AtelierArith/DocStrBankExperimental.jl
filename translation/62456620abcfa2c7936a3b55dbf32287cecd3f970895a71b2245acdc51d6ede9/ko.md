# Integers and Floating-Point Numbers

정수와 부동 소수점 값은 산술 및 계산의 기본 구성 요소입니다. 이러한 값의 내장 표현을 숫자 원시형(numeric primitives)이라고 하며, 코드에서 정수와 부동 소수점 숫자를 즉시 값으로 표현한 것을 숫자 리터럴(numeric literals)이라고 합니다. 예를 들어, `1`은 정수 리터럴이고, `1.0`은 부동 소수점 리터럴입니다. 이들의 이진 메모리 표현은 객체로서 숫자 원시형입니다.

줄리아는 광범위한 원시 숫자 유형을 제공하며, 이들에 대해 정의된 산술 및 비트 연산자와 표준 수학 함수의 전체 보완을 제공합니다. 이러한 것들은 현대 컴퓨터에서 본래 지원되는 숫자 유형 및 연산에 직접적으로 매핑되므로, 줄리아는 계산 자원을 최대한 활용할 수 있습니다. 또한, 줄리아는 [Arbitrary Precision Arithmetic](@ref)에 대한 소프트웨어 지원을 제공하여, 본래 하드웨어 표현에서 효과적으로 표현할 수 없는 숫자 값에 대한 연산을 처리할 수 있지만, 상대적으로 느린 성능의 대가가 따릅니다.

다음은 줄리아의 원시 숫자 유형입니다:

  * **정수형:**

| Type              | Signed? | Number of bits | Smallest value | Largest value |
|:----------------- |:------- |:-------------- |:-------------- |:------------- |
| [`Int8`](@ref)    | ✓       | 8              | -2^7           | 2^7 - 1       |
| [`UInt8`](@ref)   |         | 8              | 0              | 2^8 - 1       |
| [`Int16`](@ref)   | ✓       | 16             | -2^15          | 2^15 - 1      |
| [`UInt16`](@ref)  |         | 16             | 0              | 2^16 - 1      |
| [`Int32`](@ref)   | ✓       | 32             | -2^31          | 2^31 - 1      |
| [`UInt32`](@ref)  |         | 32             | 0              | 2^32 - 1      |
| [`Int64`](@ref)   | ✓       | 64             | -2^63          | 2^63 - 1      |
| [`UInt64`](@ref)  |         | 64             | 0              | 2^64 - 1      |
| [`Int128`](@ref)  | ✓       | 128            | -2^127         | 2^127 - 1     |
| [`UInt128`](@ref) |         | 128            | 0              | 2^128 - 1     |
| [`Bool`](@ref)    | N/A     | 8              | `false` (0)    | `true` (1)    |

  * **부동 소수점 유형:**

| Type              | Precision                                                                      | Number of bits |
|:----------------- |:------------------------------------------------------------------------------ |:-------------- |
| [`Float16`](@ref) | [half](https://en.wikipedia.org/wiki/Half-precision_floating-point_format)     | 16             |
| [`Float32`](@ref) | [single](https://en.wikipedia.org/wiki/Single_precision_floating-point_format) | 32             |
| [`Float64`](@ref) | [double](https://en.wikipedia.org/wiki/Double_precision_floating-point_format) | 64             |

추가적으로, [Complex and Rational Numbers](@ref)에 대한 완전한 지원은 이러한 원시 숫자 유형 위에 구축됩니다. 모든 숫자 유형은 유연하고 사용자 확장 가능한 [type promotion system](@ref conversion-and-promotion) 덕분에 명시적인 형 변환 없이 자연스럽게 상호 작용합니다.

## Integers

리터럴 정수는 표준 방식으로 표현됩니다:

```jldoctest
julia> 1
1

julia> 1234
1234
```

정수 리터럴의 기본 유형은 대상 시스템이 32비트 아키텍처인지 64비트 아키텍처인지에 따라 다릅니다:

```julia-repl
# 32-bit system:
julia> typeof(1)
Int32

# 64-bit system:
julia> typeof(1)
Int64
```

줄리아 내부 변수 [`Sys.WORD_SIZE`](@ref)는 대상 시스템이 32비트인지 64비트인지를 나타냅니다:

```julia-repl
# 32-bit system:
julia> Sys.WORD_SIZE
32

# 64-bit system:
julia> Sys.WORD_SIZE
64
```

Julia는 또한 시스템의 부호 있는 및 부호 없는 기본 정수 유형에 대한 별칭인 `Int` 및 `UInt` 유형을 정의합니다:

```julia-repl
# 32-bit system:
julia> Int
Int32
julia> UInt
UInt32

# 64-bit system:
julia> Int
Int64
julia> UInt
UInt64
```

64비트로 표현할 수 있지만 32비트로는 표현할 수 없는 더 큰 정수 리터럴은 시스템 유형에 관계없이 항상 64비트 정수를 생성합니다:

```jldoctest
# 32-bit or 64-bit system:
julia> typeof(3000000000)
Int64
```

부호 없는 정수는 `0x` 접두사와 16진수(기수 16) 숫자 `0-9a-f`를 사용하여 입력 및 출력됩니다(대문자 숫자 `A-F`도 입력에 사용할 수 있습니다). 부호 없는 값의 크기는 사용된 16진수 숫자의 수에 따라 결정됩니다:

```jldoctest
julia> x = 0x1
0x01

julia> typeof(x)
UInt8

julia> x = 0x123
0x0123

julia> typeof(x)
UInt16

julia> x = 0x1234567
0x01234567

julia> typeof(x)
UInt32

julia> x = 0x123456789abcdef
0x0123456789abcdef

julia> typeof(x)
UInt64

julia> x = 0x11112222333344445555666677778888
0x11112222333344445555666677778888

julia> typeof(x)
UInt128
```

이 행동은 정수 값을 위해 부호 없는 16진수 리터럴을 사용할 때, 일반적으로 고정된 숫자 바이트 시퀀스를 나타내기 위해 사용된다는 관찰에 기반합니다.

이진수 및 팔진수 리터럴도 지원됩니다:

```jldoctest
julia> x = 0b10
0x02

julia> typeof(x)
UInt8

julia> x = 0o010
0x08

julia> typeof(x)
UInt8

julia> x = 0x00000000000000001111222233334444
0x00000000000000001111222233334444

julia> typeof(x)
UInt128
```

16진수 리터럴에 관해서, 이진수 및 팔진수 리터럴은 부호 없는 정수 유형을 생성합니다. 이진 데이터 항목의 크기는 리터럴의 선행 숫자가 `0`이 아닐 경우 필요한 최소 크기입니다. 선행 0이 있는 경우, 크기는 동일한 길이를 가지지만 선행 숫자가 `1`인 리터럴에 대해 필요한 최소 크기로 결정됩니다. 이는 다음을 의미합니다:

  * `0x1` 및 `0x12`는 `UInt8` 리터럴입니다.
  * `0x123`와 `0x1234`는 `UInt16` 리터럴입니다.
  * `0x12345`와 `0x12345678`는 `UInt32` 리터럴입니다.
  * `0x123456789` 및 `0x1234567890adcdef`는 `UInt64` 리터럴입니다.

선행 제로 숫자가 값에 기여하지 않더라도, 리터럴의 저장 크기를 결정하는 데는 포함됩니다. 따라서 `0x01`은 `UInt8`이고 `0x0001`은 `UInt16`입니다.

사용자가 크기를 조절할 수 있도록 합니다.

부호 없는 리터럴(`0x`로 시작하는)로 인코딩된 정수 값이 `UInt128` 값으로 표현할 수 있는 범위를 초과할 경우, 대신 `BigInt` 값이 생성됩니다. 이는 부호 없는 타입은 아니지만, 그러한 큰 정수 값을 표현할 수 있는 유일한 내장 타입입니다.

이진수, 8진수 및 16진수 리터럴은 부호 없는 리터럴 바로 앞에 `-`를 붙여서 부호를 가질 수 있습니다. 이들은 부호 없는 리터럴이 생성하는 것과 동일한 크기의 부호 없는 정수를 생성하며, 값의 2의 보수를 사용합니다:

```jldoctest
julia> -0x2
0xfe

julia> -0x0002
0xfffe
```

원시 숫자 유형(예: 정수)의 최소 및 최대 표현 가능 값은 [`typemin`](@ref) 및 [`typemax`](@ref) 함수에 의해 제공됩니다:

```jldoctest
julia> (typemin(Int32), typemax(Int32))
(-2147483648, 2147483647)

julia> for T in [Int8,Int16,Int32,Int64,Int128,UInt8,UInt16,UInt32,UInt64,UInt128]
           println("$(lpad(T,7)): [$(typemin(T)),$(typemax(T))]")
       end
   Int8: [-128,127]
  Int16: [-32768,32767]
  Int32: [-2147483648,2147483647]
  Int64: [-9223372036854775808,9223372036854775807]
 Int128: [-170141183460469231731687303715884105728,170141183460469231731687303715884105727]
  UInt8: [0,255]
 UInt16: [0,65535]
 UInt32: [0,4294967295]
 UInt64: [0,18446744073709551615]
UInt128: [0,340282366920938463463374607431768211455]
```

[`typemin`](@ref)와 [`typemax`](@ref)가 반환하는 값은 항상 주어진 인수 유형입니다. (위 표현식은 [for loops](@ref man-loops), [Strings](@ref man-strings), 및 [Interpolation](@ref string-interpolation)을 포함하여 아직 도입되지 않은 여러 기능을 사용하지만, 일부 기존 프로그래밍 경험이 있는 사용자에게는 이해하기 쉬울 것입니다.)

### Overflow behavior

줄리아에서 주어진 타입의 최대 표현 가능 값을 초과하면 래핑 동작이 발생합니다:

```jldoctest
julia> x = typemax(Int64)
9223372036854775807

julia> x + 1
-9223372036854775808

julia> x + 1 == typemin(Int64)
true
```

줄리아의 정수 타입을 사용한 산술 연산은 본질적으로 [modular arithmetic](https://en.wikipedia.org/wiki/Modular_arithmetic)를 수행하며, 이는 현대 컴퓨터 하드웨어에서의 정수 산술의 특성을 반영합니다. 오버플로우가 발생할 가능성이 있는 시나리오에서는 이러한 오버플로우로 인해 발생할 수 있는 랩어라운드 효과를 명시적으로 확인하는 것이 중요합니다. [`Base.Checked`](@ref) 모듈은 오버플로우 체크가 장착된 산술 연산의 모음을 제공하며, 오버플로우가 발생할 경우 오류를 발생시킵니다. 어떤 상황에서도 오버플로우를 용인할 수 없는 사용 사례의 경우, [Arbitrary Precision Arithmetic](@ref)에서 자세히 설명된 [`BigInt`](@ref) 타입을 사용하는 것이 바람직합니다.

오버플로우 동작의 예와 이를 해결할 수 있는 방법은 다음과 같습니다:

```jldoctest
julia> 10^19
-8446744073709551616

julia> big(10)^19
10000000000000000000
```

### Division errors

정수 나눗셈(`div` 함수)에는 두 가지 예외적인 경우가 있습니다: 0으로 나누기와 가장 낮은 음수([`typemin`](@ref))를 -1로 나누기. 이 두 경우 모두 [`DivideError`](@ref)를 발생시킵니다. 나머지 및 모듈러스 함수(`rem` 및 `mod`)는 두 번째 인수가 0일 때 `4d61726b646f776e2e436f64652822222c20224469766964654572726f722229_40726566`를 발생시킵니다.

## Floating-Point Numbers

리터럴 부동 소수점 숫자는 표준 형식으로 표현되며, 필요할 경우 [E-notation](https://en.wikipedia.org/wiki/Scientific_notation#E_notation)을 사용합니다:

```jldoctest
julia> 1.0
1.0

julia> 1.
1.0

julia> 0.5
0.5

julia> .5
0.5

julia> -1.23
-1.23

julia> 1e10
1.0e10

julia> 2.5e-4
0.00025
```

위의 결과는 모두 [`Float64`](@ref) 값입니다. 리터럴 [`Float32`](@ref) 값은 `e` 대신 `f`를 써서 입력할 수 있습니다:

```jldoctest
julia> x = 0.5f0
0.5f0

julia> typeof(x)
Float32

julia> 2.5f-4
0.00025f0
```

값은 쉽게 [`Float32`](@ref)으로 변환될 수 있습니다:

```jldoctest
julia> x = Float32(-1.5)
-1.5f0

julia> typeof(x)
Float32
```

16진수 부동 소수점 리터럴도 유효하지만, [`Float64`](@ref) 값으로만 유효하며, `p`가 2진수 지수 앞에 와야 합니다:

```jldoctest
julia> 0x1p0
1.0

julia> 0x1.8p3
12.0

julia> x = 0x.4p-1
0.125

julia> typeof(x)
Float64
```

반정밀도 부동 소수점 숫자도 지원됩니다 ([`Float16`](@ref)), 하지만 소프트웨어로 구현되어 있으며 계산을 위해 [`Float32`](@ref)를 사용합니다.

```jldoctest
julia> sizeof(Float16(4.))
2

julia> 2*Float16(4.)
Float16(8.0)
```

밑줄 `_`은 숫자 구분자로 사용할 수 있습니다:

```jldoctest
julia> 10_000, 0.000_000_005, 0xdead_beef, 0b1011_0010
(10000, 5.0e-9, 0xdeadbeef, 0xb2)
```

### Floating-point zero

부동 소수점 숫자는 [two zeros](https://en.wikipedia.org/wiki/Signed_zero)를 가지고 있으며, 양의 영과 음의 영이 있습니다. 이들은 서로 같지만 서로 다른 이진 표현을 가지며, 이는 [`bitstring`](@ref) 함수를 사용하여 확인할 수 있습니다:

```jldoctest
julia> 0.0 == -0.0
true

julia> bitstring(0.0)
"0000000000000000000000000000000000000000000000000000000000000000"

julia> bitstring(-0.0)
"1000000000000000000000000000000000000000000000000000000000000000"
```

### Special floating-point values

실수선상의 어떤 점과도 대응하지 않는 세 가지 지정된 표준 부동 소수점 값이 있습니다:

| `Float16` | `Float32` | `Float64` | Name              | Description                                                     |
|:--------- |:--------- |:--------- |:----------------- |:--------------------------------------------------------------- |
| `Inf16`   | `Inf32`   | `Inf`     | positive infinity | a value greater than all finite floating-point values           |
| `-Inf16`  | `-Inf32`  | `-Inf`    | negative infinity | a value less than all finite floating-point values              |
| `NaN16`   | `NaN32`   | `NaN`     | not a number      | a value not `==` to any floating-point value (including itself) |

추가적인 논의는 이러한 비유한 부동 소수점 값들이 서로 및 다른 부동 소수점 값들과 어떻게 정렬되는지에 대해 [Numeric Comparisons](@ref)를 참조하십시오. [IEEE 754 standard](https://en.wikipedia.org/wiki/IEEE_754-2008)에 따르면, 이러한 부동 소수점 값들은 특정 산술 연산의 결과입니다:

```jldoctest
julia> 1/Inf
0.0

julia> 1/0
Inf

julia> -5/0
-Inf

julia> 0.000001/0
Inf

julia> 0/0
NaN

julia> 500 + Inf
Inf

julia> 500 - Inf
-Inf

julia> Inf + Inf
Inf

julia> Inf - Inf
NaN

julia> Inf * Inf
Inf

julia> Inf / Inf
NaN

julia> 0 * Inf
NaN

julia> NaN == NaN
false

julia> NaN != NaN
true

julia> NaN < NaN
false

julia> NaN > NaN
false
```

[`typemin`](@ref) 및 [`typemax`](@ref) 함수는 부동 소수점 유형에도 적용됩니다:

```jldoctest
julia> (typemin(Float16),typemax(Float16))
(-Inf16, Inf16)

julia> (typemin(Float32),typemax(Float32))
(-Inf32, Inf32)

julia> (typemin(Float64),typemax(Float64))
(-Inf, Inf)
```

### Machine epsilon

대부분의 실수는 부동 소수점 숫자로 정확하게 표현될 수 없으므로, 많은 용도에서 인접한 표현 가능한 부동 소수점 숫자 간의 거리를 아는 것이 중요합니다. 이는 종종 [machine epsilon](https://en.wikipedia.org/wiki/Machine_epsilon)으로 알려져 있습니다.

줄리아는 [`eps`](@ref)을 제공하며, 이는 `1.0`과 다음으로 더 큰 표현 가능한 부동 소수점 값 사이의 거리를 제공합니다:

```jldoctest
julia> eps(Float32)
1.1920929f-7

julia> eps(Float64)
2.220446049250313e-16

julia> eps() # same as eps(Float64)
2.220446049250313e-16
```

이 값들은 `2.0^-23`과 `2.0^-52`로, 각각 [`Float32`](@ref)와 [`Float64`](@ref)입니다. [`eps`](@ref) 함수는 또한 부동 소수점 값을 인수로 받을 수 있으며, 그 값과 다음으로 표현 가능한 부동 소수점 값 사이의 절대 차이를 제공합니다. 즉, `eps(x)`는 `x + eps(x)`가 `x`보다 큰 다음 표현 가능한 부동 소수점 값이 되도록 하는 `x`와 같은 유형의 값을 생성합니다:

```jldoctest
julia> eps(1.0)
2.220446049250313e-16

julia> eps(1000.)
1.1368683772161603e-13

julia> eps(1e-27)
1.793662034335766e-43

julia> eps(0.0)
5.0e-324
```

인접한 표현 가능한 부동 소수점 숫자 간의 거리는 일정하지 않으며, 작은 값에서는 더 작고 큰 값에서는 더 큽니다. 다시 말해, 표현 가능한 부동 소수점 숫자는 실수선에서 0에 가까운 곳에서 가장 밀집해 있으며, 0에서 멀어질수록 기하급수적으로 희소해집니다. 정의에 따라 `eps(1.0)`은 `eps(Float64)`와 동일하며, `1.0`은 64비트 부동 소수점 값입니다.

줄리아는 또한 인수에 대해 각각 다음으로 가장 큰 또는 작은 표현 가능한 부동 소수점 숫자를 반환하는 [`nextfloat`](@ref) 및 [`prevfloat`](@ref) 함수를 제공합니다:

```jldoctest
julia> x = 1.25f0
1.25f0

julia> nextfloat(x)
1.2500001f0

julia> prevfloat(x)
1.2499999f0

julia> bitstring(prevfloat(x))
"00111111100111111111111111111111"

julia> bitstring(x)
"00111111101000000000000000000000"

julia> bitstring(nextfloat(x))
"00111111101000000000000000000001"
```

이 예시는 인접한 표현 가능한 부동 소수점 숫자가 인접한 이진 정수 표현도 갖는다는 일반 원칙을 강조합니다.

### Rounding modes

숫자가 정확한 부동 소수점 표현을 가지지 않는 경우, 적절한 표현 가능한 값으로 반올림해야 합니다. 그러나 이 반올림 방식은 필요에 따라 [IEEE 754 standard](https://en.wikipedia.org/wiki/IEEE_754-2008)에 제시된 반올림 모드에 따라 변경될 수 있습니다.

기본적으로 사용되는 모드는 항상 [`RoundNearest`](@ref)이며, 이는 표현 가능한 값에 가장 가까운 값으로 반올림되며, 동점일 경우 가장 가까운 짝수 최하위 비트를 가진 값으로 반올림됩니다.

### Background and References

부동 소수점 산술은 저수준 구현 세부 사항에 익숙하지 않은 사용자에게 놀라운 많은 미묘함을 포함합니다. 그러나 이러한 미묘함은 대부분의 과학 계산 관련 서적에서 자세히 설명되어 있으며, 다음 참고 문헌에서도 설명되어 있습니다:

  * 부동 소수점 산술에 대한 확정적인 가이드는 [IEEE 754-2008 Standard](https://standards.ieee.org/standard/754-2008.html)입니다. 그러나 온라인에서 무료로 제공되지 않습니다.
  * 부동 소수점 숫자가 어떻게 표현되는지에 대한 간결하고 명확한 설명은 John D. Cook의 [article](https://www.johndcook.com/blog/2009/04/06/anatomy-of-a-floating-point-number/)를 참조하십시오. 또한 그의 [introduction](https://www.johndcook.com/blog/2009/04/06/numbers-are-a-leaky-abstraction/)는 이 표현이 실제 숫자의 이상화된 추상화와 어떻게 다른지에서 발생하는 몇 가지 문제를 다룹니다.
  * 또한 추천하는 것은 Bruce Dawson의 [series of blog posts on floating-point numbers](https://randomascii.wordpress.com/2012/05/20/thats-not-normalthe-performance-of-odd-floats/).
  * 우수하고 심도 있는 부동 소수점 숫자 및 이와 관련된 수치 정확성 문제에 대한 논의는 David Goldberg의 논문을 참조하십시오 [What Every Computer Scientist Should Know About Floating-Point Arithmetic](https://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.22.6768&rep=rep1&type=pdf).
  * 더 광범위한 부동 소수점 숫자의 역사, 이론 및 문제에 대한 문서와 수치 계산의 많은 다른 주제에 대한 논의는 [collected writings](https://people.eecs.berkeley.edu/~wkahan/)를 참조하십시오. 이는 [William Kahan](https://en.wikipedia.org/wiki/William_Kahan)로 일반적으로 알려진 "부동 소수점의 아버지"입니다. 특히 관심이 있을 수 있는 것은 [An Interview with the Old Man of Floating-Point](https://people.eecs.berkeley.edu/~wkahan/ieee754status/754story.html)입니다.

## Arbitrary Precision Arithmetic

임의 정밀도 정수 및 부동 소수점 수로 계산을 허용하기 위해, Julia는 각각 [GNU Multiple Precision Arithmetic Library (GMP)](https://gmplib.org) 및 [GNU MPFR Library](https://www.mpfr.org)를 래핑합니다. [`BigInt`](@ref) 및 [`BigFloat`](@ref) 유형은 각각 임의 정밀도 정수 및 부동 소수점 수에 대해 Julia에서 사용할 수 있습니다.

생성자는 원시 숫자 유형에서 이러한 유형을 생성하기 위해 존재하며, [string literal](@ref non-standard-string-literals) [`@big_str`](@ref) 또는 [`parse`](@ref)를 사용하여 `AbstractString`에서 생성할 수 있습니다. `BigInt`는 다른 내장 정수 유형으로는 너무 큰 경우 정수 리터럴로 입력할 수도 있습니다. `Base`에는 부호 없는 임의 정밀도 정수 유형이 없으므로(`BigInt`는 대부분의 경우 충분함), 16진수, 8진수 및 2진수 리터럴을 사용할 수 있습니다(10진수 리터럴 외에도).

한 번 생성되면, 그들은 줄리아의 [type promotion and conversion mechanism](@ref conversion-and-promotion) 덕분에 모든 다른 숫자 유형과 산술에 참여합니다:

```jldoctest
julia> BigInt(typemax(Int64)) + 1
9223372036854775808

julia> big"123456789012345678901234567890" + 1
123456789012345678901234567891

julia> parse(BigInt, "123456789012345678901234567890") + 1
123456789012345678901234567891

julia> string(big"2"^200, base=16)
"100000000000000000000000000000000000000000000000000"

julia> 0x100000000000000000000000000000000-1 == typemax(UInt128)
true

julia> 0x000000000000000000000000000000000
0

julia> typeof(ans)
BigInt

julia> big"1.23456789012345678901"
1.234567890123456789010000000000000000000000000000000000000000000000000000000004

julia> parse(BigFloat, "1.23456789012345678901")
1.234567890123456789010000000000000000000000000000000000000000000000000000000004

julia> BigFloat(2.0^66) / 3
2.459565876494606882133333333333333333333333333333333333333333333333333333333344e+19

julia> factorial(BigInt(40))
815915283247897734345611269596115894272000000000
```

However, type promotion between the primitive types above and [`BigInt`](@ref)/[`BigFloat`](@ref) is not automatic and must be explicitly stated.

```jldoctest
julia> x = typemin(Int64)
-9223372036854775808

julia> x = x - 1
9223372036854775807

julia> typeof(x)
Int64

julia> y = BigInt(typemin(Int64))
-9223372036854775808

julia> y = y - 1
-9223372036854775809

julia> typeof(y)
BigInt
```

[`BigFloat`](@ref) 연산의 기본 정밀도(유효 숫자의 비트 수)와 반올림 모드는 [`setprecision`](@ref) 및 [`setrounding`](@ref)를 호출하여 전역적으로 변경할 수 있으며, 이후의 모든 계산은 이러한 변경 사항을 고려합니다. 또는, 특정 코드 블록의 실행 내에서만 정밀도나 반올림을 변경하려면 `do` 블록과 함께 동일한 함수를 사용할 수 있습니다:

```jldoctest
julia> setrounding(BigFloat, RoundUp) do
           BigFloat(1) + parse(BigFloat, "0.1")
       end
1.100000000000000000000000000000000000000000000000000000000000000000000000000003

julia> setrounding(BigFloat, RoundDown) do
           BigFloat(1) + parse(BigFloat, "0.1")
       end
1.099999999999999999999999999999999999999999999999999999999999999999999999999986

julia> setprecision(40) do
           BigFloat(1) + parse(BigFloat, "0.1")
       end
1.1000000000004
```

!!! warning
    [`setprecision`](@ref) 또는 [`setrounding`](@ref)와 [`@big_str`](@ref) 간의 관계는 `big` 문자열 리터럴(예: `big"0.3"`)에 사용되는 매크로와 관련하여 직관적이지 않을 수 있습니다. 이는 `@big_str`가 매크로라는 사실의 결과입니다. 자세한 내용은 `4d61726b646f776e2e436f64652822222c2022406269675f7374722229_40726566` 문서를 참조하십시오.


## [Numeric Literal Coefficients](@id man-numeric-literal-coefficients)

일반적인 수치 공식과 표현을 더 명확하게 만들기 위해, Julia는 변수가 숫자 리터럴 바로 앞에 올 수 있도록 허용하여 곱셈을 암시합니다. 이는 다항식 표현을 훨씬 깔끔하게 작성할 수 있게 합니다:

```jldoctest numeric-coefficients
julia> x = 3
3

julia> 2x^2 - 3x + 1
10

julia> 1.5x^2 - .5x + 1
13.0
```

지수 함수를 작성하는 것도 더 우아하게 만듭니다:

```jldoctest numeric-coefficients
julia> 2^2x
64
```

숫자 리터럴 계수의 우선순위는 부정과 같은 단항 연산자보다 약간 낮습니다. 따라서 `-2x`는 `(-2) * x`로 해석되고, `√2x`는 `(√2) * x`로 해석됩니다. 그러나 숫자 리터럴 계수는 지수와 결합될 때 단항 연산자와 유사하게 해석됩니다. 예를 들어 `2^3x`는 `2^(3x)`로 해석되고, `2x^3`은 `2*(x^3)`로 해석됩니다.

숫자 리터럴은 괄호로 묶인 표현식의 계수로도 작동합니다:

```jldoctest numeric-coefficients
julia> 2(x-1)^2 - 3(x-1) + 1
3
```

!!! note
    숫자 리터럴 계수의 암시적 곱셈에 사용되는 우선순위는 곱셈(`*`), 나눗셈(`/`, `\`, 및 `//`)과 같은 다른 이항 연산자보다 높습니다. 예를 들어, `1 / 2im`은 `-0.5im`과 같고, `6 // 2(2 + 1)`은 `1 // 1`과 같습니다.


또한, 괄호로 묶인 표현식은 변수에 대한 계수로 사용될 수 있으며, 이는 표현식이 변수와 곱해짐을 의미합니다:

```jldoctest numeric-coefficients
julia> (x-1)x
6
```

두 개의 괄호로 묶인 표현을 나란히 배치하거나, 괄호로 묶인 표현 앞에 변수를 놓는 것만으로는 곱셈을 암시할 수 없다:

```jldoctest numeric-coefficients
julia> (x-1)(x+1)
ERROR: MethodError: objects of type Int64 are not callable

julia> x(x+1)
ERROR: MethodError: objects of type Int64 are not callable
```

두 표현식은 함수 적용으로 해석됩니다: 숫자 리터럴이 아닌 모든 표현식은 괄호가 바로 뒤따를 경우 괄호 안의 값에 적용되는 함수로 해석됩니다 (함수에 대한 자세한 내용은 [Functions](@ref)을 참조하십시오). 따라서 이 두 경우 모두 왼쪽 값이 함수가 아니기 때문에 오류가 발생합니다.

위의 구문 향상은 일반적인 수학 공식을 작성할 때 발생하는 시각적 잡음을 크게 줄여줍니다. 숫자 리터럴 계수와 그것이 곱하는 식별자 또는 괄호로 묶인 표현 사이에 공백이 올 수 없다는 점에 유의하십시오.

### Syntax Conflicts

대조된 리터럴 계수 구문은 일부 숫자 리터럴 구문과 충돌할 수 있습니다: 16진수, 8진수 및 이진 정수 리터럴과 부동 소수점 리터럴에 대한 공학 표기법. 다음은 구문 충돌이 발생하는 몇 가지 상황입니다:

  * 16진수 정수 리터럴 표현 `0xff`는 숫자 리터럴 `0`에 변수 `xff`를 곱한 것으로 해석될 수 있습니다. `0o777` 또는 `0b01001010`과 같은 8진수 및 이진수 리터럴에서도 유사한 모호성이 발생합니다.
  * 부동 소수점 리터럴 표현식 `1e10`은 숫자 리터럴 `1`이 변수 `e10`과 곱해진 것으로 해석될 수 있으며, 이와 유사하게 동등한 `E` 형식에서도 마찬가지입니다.
  * 32비트 부동 소수점 리터럴 표현 `1.5f22`는 숫자 리터럴 `1.5`에 변수 `f22`를 곱한 것으로 해석될 수 있습니다.

모든 경우에 모호성은 숫자 리터럴로 해석하는 쪽으로 해결됩니다:

  * `0x`/`0o`/`0b`로 시작하는 표현식은 항상 16진수/8진수/2진수 리터럴입니다.
  * 숫자 리터럴로 시작하고 `e` 또는 `E`가 뒤따르는 표현식은 항상 부동 소수점 리터럴입니다.
  * 숫자 리터럴로 시작하고 `f`로 끝나는 표현식은 항상 32비트 부동 소수점 리터럴입니다.

`E`와 달리, 역사적인 이유로 숫자 리터럴에서 `e`와 동등한 `E`는 `F`가 단순한 문자일 뿐이며 숫자 리터럴에서 `f`처럼 동작하지 않습니다. 따라서 숫자 리터럴로 시작하고 그 뒤에 `F`가 오는 표현식은 숫자 리터럴에 변수를 곱한 것으로 해석됩니다. 즉, 예를 들어 `1.5F22`는 `1.5 * F22`와 같습니다.

## Literal zero and one

Julia는 지정된 유형 또는 주어진 변수의 유형에 해당하는 리터럴 0과 1을 반환하는 함수를 제공합니다.

| Function          | Description                                      |
|:----------------- |:------------------------------------------------ |
| [`zero(x)`](@ref) | Literal zero of type `x` or type of variable `x` |
| [`one(x)`](@ref)  | Literal one of type `x` or type of variable `x`  |

이 함수들은 불필요한 [type conversion](@ref conversion-and-promotion)로 인한 오버헤드를 피하기 위해 [Numeric Comparisons](@ref)에서 유용합니다.

예시:

```jldoctest
julia> zero(Float32)
0.0f0

julia> zero(1.0)
0.0

julia> one(Int32)
1

julia> one(BigFloat)
1.0
```
