# Complex and Rational Numbers

줄리아는 복소수와 유리수에 대한 미리 정의된 유형을 포함하고 있으며, 이들에 대해 모든 표준 [Mathematical Operations and Elementary Functions](@ref)을 지원합니다. [Conversion and Promotion](@ref conversion-and-promotion)은 기본 또는 복합 미리 정의된 숫자 유형의 조합에 대한 연산이 예상대로 작동하도록 정의되어 있습니다.

## Complex Numbers

전역 상수 [`im`](@ref)는 복소수 *i*에 바인딩되어 있으며, 이는 -1의 주 제곱근을 나타냅니다. (수학자들이 사용하는 `i` 또는 엔지니어들이 사용하는 `j`를 이 전역 상수에 사용하기로 한 것은 이러한 이름들이 매우 일반적인 인덱스 변수 이름이기 때문에 거부되었습니다.) 줄리아는 숫자 리터럴을 [juxtaposed with identifiers as coefficients](@ref man-numeric-literal-coefficients)와 같이 허용하므로, 이 바인딩은 전통적인 수학적 표기법과 유사하게 복소수에 대한 편리한 구문을 제공합니다:

```jldoctest
julia> 1+2im
1 + 2im
```

복소수로 모든 표준 산술 연산을 수행할 수 있습니다:

```jldoctest
julia> (1 + 2im)*(2 - 3im)
8 + 1im

julia> (1 + 2im)/(1 - 2im)
-0.6 + 0.8im

julia> (1 + 2im) + (1 - 2im)
2 + 0im

julia> (-3 + 2im) - (5 - 1im)
-8 + 3im

julia> (-1 + 2im)^2
-3 - 4im

julia> (-1 + 2im)^2.5
2.729624464784009 - 6.9606644595719im

julia> (-1 + 2im)^(1 + 1im)
-0.27910381075826657 + 0.08708053414102428im

julia> 3(2 - 5im)
6 - 15im

julia> 3(2 - 5im)^2
-63 - 60im

julia> 3(2 - 5im)^-1.0
0.20689655172413793 + 0.5172413793103449im
```

프로모션 메커니즘은 서로 다른 유형의 피연산자 조합이 제대로 작동하도록 보장합니다:

```jldoctest
julia> 2(1 - 1im)
2 - 2im

julia> (2 + 3im) - 1
1 + 3im

julia> (1 + 2im) + 0.5
1.5 + 2.0im

julia> (2 + 3im) - 0.5im
2.0 + 2.5im

julia> 0.75(1 + 2im)
0.75 + 1.5im

julia> (2 + 3im) / 2
1.0 + 1.5im

julia> (1 - 3im) / (2 + 2im)
-0.5 - 1.0im

julia> 2im^2
-2 + 0im

julia> 1 + 3/4im
1.0 - 0.75im
```

`3/4im == 3/(4*im) == -(3/4*im)`이라는 점에 유의하세요. 리터럴 계수가 나눗셈보다 더 강하게 결합되기 때문입니다.

복소 값을 조작하기 위한 표준 함수가 제공됩니다:

```jldoctest
julia> z = 1 + 2im
1 + 2im

julia> real(1 + 2im) # real part of z
1

julia> imag(1 + 2im) # imaginary part of z
2

julia> conj(1 + 2im) # complex conjugate of z
1 - 2im

julia> abs(1 + 2im) # absolute value of z
2.23606797749979

julia> abs2(1 + 2im) # squared absolute value
5

julia> angle(1 + 2im) # phase angle in radians
1.1071487177940904
```

As usual, the absolute value ([`abs`](@ref)) of a complex number is its distance from zero. [`abs2`](@ref) gives the square of the absolute value, and is of particular use for complex numbers since it avoids taking a square root. [`angle`](@ref) returns the phase angle in radians (also known as the *argument* or *arg* function). The full gamut of other [Elementary Functions](@ref) is also defined for complex numbers:

```jldoctest
julia> sqrt(1im)
0.7071067811865476 + 0.7071067811865475im

julia> sqrt(1 + 2im)
1.272019649514069 + 0.7861513777574233im

julia> cos(1 + 2im)
2.0327230070196656 - 3.0518977991517997im

julia> exp(1 + 2im)
-1.1312043837568135 + 2.4717266720048188im

julia> sinh(1 + 2im)
-0.4890562590412937 + 1.4031192506220405im
```

수학 함수는 일반적으로 실수에 적용될 때 실수 값을 반환하고, 복소수에 적용될 때 복소수 값을 반환한다는 점에 유의하십시오. 예를 들어, [`sqrt`](@ref)는 `-1`과 `-1 + 0im`에 적용될 때 다르게 동작합니다. 비록 `-1 == -1 + 0im`이지만 말입니다.

```jldoctest
julia> sqrt(-1)
ERROR: DomainError with -1.0:
sqrt was called with a negative real argument but will only return a complex result if called with a complex argument. Try sqrt(Complex(x)).
Stacktrace:
[...]

julia> sqrt(-1 + 0im)
0.0 + 1.0im
```

[literal numeric coefficient notation](@ref man-numeric-literal-coefficients)는 변수를 사용하여 복소수를 구성할 때 작동하지 않습니다. 대신, 곱셈은 명시적으로 작성해야 합니다:

```jldoctest
julia> a = 1; b = 2; a + b*im
1 + 2im
```

그러나, 이는 *권장되지* 않습니다. 대신, [`complex`](@ref) 함수를 사용하여 복소 값을 실수 부분과 허수 부분에서 직접 구성하는 것이 더 효율적입니다:

```jldoctest
julia> a = 1; b = 2; complex(a, b)
1 + 2im
```

이 구조는 곱셈 및 덧셈 연산을 피합니다.

[`Inf`](@ref) 및 [`NaN`](@ref)는 [Special floating-point values](@ref) 섹션에 설명된 대로 복소수의 실수 및 허수 부분을 통해 전파됩니다:

```jldoctest
julia> 1 + Inf*im
1.0 + Inf*im

julia> 1 + NaN*im
1.0 + NaN*im
```

## Rational Numbers

줄리아는 정수의 정확한 비율을 나타내기 위해 유리수 유형을 가지고 있습니다. 유리수는 [`//`](@ref) 연산자를 사용하여 생성됩니다:

```jldoctest
julia> 2//3
2//3
```

유리수의 분자와 분모에 공통 인수가 있는 경우, 분모가 음수가 되지 않도록 가장 낮은 항으로 약분됩니다:

```jldoctest
julia> 6//9
2//3

julia> -4//8
-1//2

julia> 5//-15
-1//3

julia> -4//-12
1//3
```

이 정규화된 정수 비율의 형태는 고유하므로, 유리 값의 동등성은 분자와 분모의 동등성을 확인함으로써 테스트할 수 있습니다. 유리 값의 표준화된 분자와 분모는 [`numerator`](@ref) 및 [`denominator`](@ref) 함수를 사용하여 추출할 수 있습니다:

```jldoctest
julia> numerator(2//3)
2

julia> denominator(2//3)
3
```

분자와 분모의 직접 비교는 일반적으로 필요하지 않습니다. 왜냐하면 표준 산술 및 비교 연산이 유리수에 대해 정의되어 있기 때문입니다:

```jldoctest
julia> 2//3 == 6//9
true

julia> 2//3 == 9//27
false

julia> 3//7 < 1//2
true

julia> 3//4 > 2//3
true

julia> 2//4 + 1//6
2//3

julia> 5//12 - 1//4
1//6

julia> 5//8 * 3//12
5//32

julia> 6//5 / 10//7
21//25
```

유리수는 쉽게 부동 소수점 숫자로 변환될 수 있습니다:

```jldoctest
julia> float(3//4)
0.75
```

유리수에서 부동 소수점으로의 변환은 `a`와 `b`의 모든 정수 값에 대해 다음 항등식을 준수합니다. 단, `a==0 && b <= 0`인 경우는 제외합니다:

```jldoctest
julia> a = 1; b = 2;

julia> isequal(float(a//b), a/b)
true

julia> a, b = 0, 0
(0, 0)

julia> float(a//b)
ERROR: ArgumentError: invalid rational: zero(Int64)//zero(Int64)
Stacktrace:
[...]

julia> a/b
NaN

julia> a, b = 0, -1
(0, -1)

julia> float(a//b), a/b
(0.0, -0.0)
```

무한한 유리값을 구성하는 것은 허용됩니다:

```jldoctest
julia> 5//0
1//0

julia> x = -3//0
-1//0

julia> typeof(x)
Rational{Int64}
```

[`NaN`](@ref)의 유리 값을 구성하려고 하지만, 유효하지 않습니다:

```jldoctest
julia> 0//0
ERROR: ArgumentError: invalid rational: zero(Int64)//zero(Int64)
Stacktrace:
[...]
```

평소와 같이, 프로모션 시스템은 다른 숫자 유형과의 상호작용을 수월하게 만듭니다:

```jldoctest
julia> 3//5 + 1
8//5

julia> 3//5 - 0.5
0.09999999999999998

julia> 2//7 * (1 + 2im)
2//7 + 4//7*im

julia> 2//7 * (1.5 + 2im)
0.42857142857142855 + 0.5714285714285714im

julia> 3//2 / (1 + 2im)
3//10 - 3//5*im

julia> 1//2 + 2im
1//2 + 2//1*im

julia> 1 + 2//3im
1//1 - 2//3*im

julia> 0.5 == 1//2
true

julia> 0.33 == 1//3
false

julia> 0.33 < 1//3
true

julia> 1//3 - 0.33
0.0033333333333332993
```
