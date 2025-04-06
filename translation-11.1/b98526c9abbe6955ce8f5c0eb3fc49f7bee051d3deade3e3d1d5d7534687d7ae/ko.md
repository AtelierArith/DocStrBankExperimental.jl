# [Constructors](@id man-constructors)

생성자 [^1]는 새로운 객체를 생성하는 함수입니다. 구체적으로는 [Composite Types](@ref)의 인스턴스입니다. Julia에서 타입 객체는 생성자 함수 역할도 합니다. 이는 인수 튜플에 함수로 적용될 때 자신들의 새로운 인스턴스를 생성합니다. 복합 타입이 소개될 때 이미 간단히 언급된 내용입니다. 예를 들어:

```jldoctest footype
julia> struct Foo
           bar
           baz
       end

julia> foo = Foo(1, 2)
Foo(1, 2)

julia> foo.bar
1

julia> foo.baz
2
```

많은 유형의 경우, 필드 값을 결합하여 새로운 객체를 형성하는 것만으로 인스턴스를 생성하는 데 필요한 모든 것이 충족됩니다. 그러나 복합 객체를 생성할 때 더 많은 기능이 필요한 경우도 있습니다. 때때로 불변 조건을 강제해야 하며, 이는 인수를 확인하거나 변환함으로써 이루어질 수 있습니다. [Recursive data structures](https://en.wikipedia.org/wiki/Recursion_%28computer_science%29#Recursive_data_structures_.28structural_recursion.29), 특히 자기 참조일 수 있는 객체는 종종 불완전한 상태로 먼저 생성한 다음 프로그래밍적으로 수정하여 완전하게 만들어야만 깔끔하게 구성할 수 있습니다. 이는 객체 생성과는 별도의 단계입니다. 때때로 필드보다 적거나 다른 유형의 매개변수로 객체를 구성할 수 있는 것이 편리합니다. 줄리아의 객체 구성 시스템은 이러한 모든 경우와 그 이상을 다룹니다.

[^1]: Nomenclature: while the term "constructor" generally refers to the entire function which constructs objects of a type, it is common to abuse terminology slightly and refer to specific constructor methods as "constructors". In such situations, it is generally clear from the context that the term is used to mean "constructor method" rather than "constructor function", especially as it is often used in the sense of singling out a particular method of the constructor from all of the others.

## [Outer Constructor Methods](@id man-outer-constructor-methods)

생성자는 줄리아의 다른 함수와 마찬가지로 그 전체 동작이 메서드의 결합된 동작에 의해 정의됩니다. 따라서 새로운 메서드를 정의함으로써 생성자에 기능을 추가할 수 있습니다. 예를 들어, `Foo` 객체에 대해 하나의 인수만 받고 주어진 값을 `bar`와 `baz` 필드 모두에 사용하는 생성자 메서드를 추가하고 싶다고 가정해 보겠습니다. 이는 간단합니다:

```jldoctest footype
julia> Foo(x) = Foo(x,x)
Foo

julia> Foo(1)
Foo(1, 1)
```

`bar`와 `baz` 필드에 대한 기본 값을 제공하는 인수가 없는 `Foo` 생성자 메서드를 추가할 수도 있습니다:

```jldoctest footype
julia> Foo() = Foo(0)
Foo

julia> Foo()
Foo(0, 0)
```

여기서 매개변수가 없는 생성자 메서드는 매개변수가 하나인 생성자 메서드를 호출하고, 이 메서드는 다시 자동으로 제공되는 매개변수가 두 개인 생성자 메서드를 호출합니다. 곧 명확해질 이유로, 이렇게 일반 메서드로 선언된 추가 생성자 메서드는 *외부* 생성자 메서드라고 불립니다. 외부 생성자 메서드는 자동으로 제공되는 기본 생성자와 같은 다른 생성자 메서드를 호출하여 새로운 인스턴스를 생성할 수 있습니다.

## [Inner Constructor Methods](@id man-inner-constructor-methods)

외부 생성자 메서드는 객체를 구성하기 위한 추가 편의 메서드를 제공하는 문제를 해결하는 데 성공하지만, 이 장의 서두에서 언급한 다른 두 가지 사용 사례인 불변 조건 강제와 자기 참조 객체의 구성을 해결하지 못합니다. 이러한 문제를 해결하기 위해서는 *내부* 생성자 메서드가 필요합니다. 내부 생성자 메서드는 외부 생성자 메서드와 유사하지만 두 가지 차이점이 있습니다:

1. 타입 선언 블록 내부에 선언되며, 일반 메서드처럼 외부에 선언되지 않습니다.
2. 특별히 존재하는 함수 [`new`](@ref)에 접근할 수 있으며, 이 함수는 블록의 유형 객체를 생성합니다.

예를 들어, 첫 번째 숫자가 두 번째 숫자보다 크지 않다는 제약 조건을 가진 실수 쌍을 보유하는 타입을 선언하고자 한다고 가정해 보겠습니다. 다음과 같이 선언할 수 있습니다:

```jldoctest pairtype
julia> struct OrderedPair
           x::Real
           y::Real
           OrderedPair(x,y) = x > y ? error("out of order") : new(x,y)
       end
```

이제 `OrderedPair` 객체는 `x <= y`인 경우에만 생성할 수 있습니다:

```jldoctest pairtype; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> OrderedPair(1, 2)
OrderedPair(1, 2)

julia> OrderedPair(2,1)
ERROR: out of order
Stacktrace:
 [1] error at ./error.jl:33 [inlined]
 [2] OrderedPair(::Int64, ::Int64) at ./none:4
 [3] top-level scope
```

타입이 `mutable`로 선언되었다면, 필드 값을 직접 변경하여 이 불변성을 위반할 수 있습니다. 물론, 객체의 내부를 무단으로 건드리는 것은 나쁜 관행입니다. 당신(또는 다른 누군가)은 나중에 추가적인 외부 생성자 메서드를 제공할 수도 있지만, 일단 타입이 선언되면 더 이상 내부 생성자 메서드를 추가할 수 있는 방법은 없습니다. 외부 생성자 메서드는 다른 생성자 메서드를 호출하여 객체를 생성할 수만 있기 때문에, 궁극적으로는 객체를 생성하기 위해 어떤 내부 생성자가 호출되어야 합니다. 이는 선언된 타입의 모든 객체가 해당 타입에 제공된 내부 생성자 메서드 중 하나의 호출을 통해 존재해야 함을 보장하여, 타입의 불변성을 어느 정도 강제합니다.

내부 생성자 메서드가 정의되면 기본 생성자 메서드는 제공되지 않습니다. 이는 필요한 모든 내부 생성자를 스스로 제공했다고 가정합니다. 기본 생성자는 객체의 모든 필드를 매개변수로 받는 내부 생성자 메서드를 작성하는 것과 동일하며(해당 필드에 타입이 있는 경우 올바른 타입으로 제한됨), 이를 `new`에 전달하여 결과 객체를 반환합니다:

```jldoctest
julia> struct Foo
           bar
           baz
           Foo(bar,baz) = new(bar,baz)
       end

```

이 선언은 명시적인 내부 생성자 메서드가 없는 `Foo` 타입의 이전 정의와 동일한 효과를 가집니다. 다음 두 타입은 동등합니다 – 하나는 기본 생성자를 가지고 있고, 다른 하나는 명시적인 생성자를 가지고 있습니다:

```jldoctest
julia> struct T1
           x::Int64
       end

julia> struct T2
           x::Int64
           T2(x) = new(x)
       end

julia> T1(1)
T1(1)

julia> T2(1)
T2(1)

julia> T1(1.0)
T1(1)

julia> T2(1.0)
T2(1)
```

내부 생성자 메서드는 가능한 한 적게 제공하는 것이 좋은 관행입니다: 모든 인수를 명시적으로 받고 필수 오류 검사 및 변환을 시행하는 것만 포함해야 합니다. 기본값이나 보조 변환을 제공하는 추가 편의 생성자 메서드는 내부 생성자를 호출하여 주요 작업을 수행하는 외부 생성자로 제공되어야 합니다. 이러한 분리는 일반적으로 매우 자연스럽습니다.

## Incomplete Initialization

최종적으로 아직 해결되지 않은 문제는 자기 참조 객체, 또는 더 일반적으로 재귀 데이터 구조의 구성입니다. 근본적인 어려움이 즉시 명확하지 않을 수 있으므로, 간단히 설명하겠습니다. 다음의 재귀 타입 선언을 고려해 보십시오:

```jldoctest selfrefer
julia> mutable struct SelfReferential
           obj::SelfReferential
       end

```

이 유형은 충분히 무해해 보일 수 있지만, 이를 인스턴스화하는 방법을 고려하면 그렇지 않습니다. 만약 `a`가 `SelfReferential`의 인스턴스라면, 두 번째 인스턴스는 다음 호출로 생성할 수 있습니다:

```julia-repl
julia> b = SelfReferential(a)
```

하지만 `obj` 필드에 대한 유효한 값을 제공할 인스턴스가 존재하지 않을 때, 첫 번째 인스턴스를 어떻게 구성할 수 있을까요? 유일한 해결책은 `obj` 필드가 할당되지 않은 불완전하게 초기화된 `SelfReferential` 인스턴스를 생성할 수 있도록 허용하고, 그 불완전한 인스턴스를 다른 인스턴스의 `obj` 필드에 대한 유효한 값으로 사용하는 것입니다. 예를 들어, 그것이 바로 자기 자신일 수 있습니다.

불완전하게 초기화된 객체의 생성을 허용하기 위해, Julia는 [`new`](@ref) 함수를 타입이 가진 필드 수보다 적은 수의 인수로 호출할 수 있도록 허용하며, 이 경우 지정되지 않은 필드는 초기화되지 않은 객체를 반환합니다. 그런 다음 내부 생성자 메서드는 불완전한 객체를 사용하여 초기화를 마친 후 반환할 수 있습니다. 여기, 예를 들어, `SelfReferential` 타입을 정의하려는 또 다른 시도가 있으며, 이번에는 인수가 없는 내부 생성자가 `obj` 필드가 자신을 가리키는 인스턴스를 반환합니다:

```jldoctest selfrefer2
julia> mutable struct SelfReferential
           obj::SelfReferential
           SelfReferential() = (x = new(); x.obj = x)
       end

```

이 생성자가 작동하고 실제로 자기 참조적인 객체를 생성한다는 것을 확인할 수 있습니다:

```jldoctest selfrefer2
julia> x = SelfReferential();

julia> x === x
true

julia> x === x.obj
true

julia> x === x.obj.obj
true
```

일반적으로 내부 생성자에서 완전히 초기화된 객체를 반환하는 것이 좋은 아이디어이지만, 불완전하게 초기화된 객체를 반환하는 것도 가능합니다:

```jldoctest incomplete
julia> mutable struct Incomplete
           data
           Incomplete() = new()
       end

julia> z = Incomplete();
```

초기화되지 않은 필드로 객체를 생성하는 것은 허용되지만, 초기화되지 않은 참조에 접근하는 것은 즉시 오류입니다:

```jldoctest incomplete
julia> z.data
ERROR: UndefRefError: access to undefined reference
```

이것은 `null` 값을 지속적으로 확인할 필요성을 피합니다. 그러나 모든 객체 필드가 참조는 아닙니다. Julia는 일부 유형을 "일반 데이터"로 간주하며, 이는 모든 데이터가 자가 포함되어 있고 다른 객체를 참조하지 않음을 의미합니다. 일반 데이터 유형은 원시 유형(예: `Int`)과 다른 일반 데이터 유형의 불변 구조체로 구성됩니다(참조: [`isbits`](@ref), [`isbitstype`](@ref)). 일반 데이터 유형의 초기 내용은 정의되지 않았습니다:

```julia-repl
julia> struct HasPlain
           n::Int
           HasPlain() = new()
       end

julia> HasPlain()
HasPlain(438103441441)
```

단순 데이터 타입의 배열은 동일한 동작을 나타냅니다.

내부 생성자에서 다른 함수로 불완전한 객체를 전달하여 그들의 완성을 위임할 수 있습니다:

```jldoctest
julia> mutable struct Lazy
           data
           Lazy(v) = complete_me(new(), v)
       end
```

생성자에서 반환된 불완전한 객체와 마찬가지로, `complete_me` 또는 그 호출자가 `Lazy` 객체의 `data` 필드에 접근하려고 시도할 경우 초기화되기 전에 즉시 오류가 발생합니다.

## Parametric Constructors

매개변수 유형은 생성자 이야기에서 몇 가지 복잡함을 추가합니다. [Parametric Types](@ref)에서 기억하듯이, 기본적으로 매개변수 복합 유형의 인스턴스는 명시적으로 주어진 유형 매개변수로 또는 생성자에 주어진 인수의 유형에 의해 암시된 유형 매개변수로 생성될 수 있습니다. 다음은 몇 가지 예입니다:

```jldoctest parametric; filter = r"Closest candidates.*\n  .*"
julia> struct Point{T<:Real}
           x::T
           y::T
       end

julia> Point(1,2) ## implicit T ##
Point{Int64}(1, 2)

julia> Point(1.0,2.5) ## implicit T ##
Point{Float64}(1.0, 2.5)

julia> Point(1,2.5) ## implicit T ##
ERROR: MethodError: no method matching Point(::Int64, ::Float64)
The type `Point` exists, but no method is defined for this combination of argument types when trying to construct it.

Closest candidates are:
  Point(::T, ::T) where T<:Real at none:2

julia> Point{Int64}(1, 2) ## explicit T ##
Point{Int64}(1, 2)

julia> Point{Int64}(1.0,2.5) ## explicit T ##
ERROR: InexactError: Int64(2.5)
Stacktrace:
[...]

julia> Point{Float64}(1.0, 2.5) ## explicit T ##
Point{Float64}(1.0, 2.5)

julia> Point{Float64}(1,2) ## explicit T ##
Point{Float64}(1.0, 2.0)
```

명시적 타입 매개변수가 있는 생성자 호출의 경우, 인수는 암시된 필드 타입으로 변환됩니다: `Point{Int64}(1,2)`는 작동하지만 `Point{Int64}(1.0,2.5)`는 [`InexactError`](@ref)를 발생시킵니다. 이는 `2.5`를 [`Int64`](@ref)로 변환할 때 발생합니다. 생성자 호출의 인수에 의해 타입이 암시되는 경우, 예를 들어 `Point(1,2)`와 같이, 인수의 타입이 일치해야 합니다 – 그렇지 않으면 `T`를 결정할 수 없습니다 – 그러나 일치하는 타입을 가진 실수 인수의 쌍은 일반 `Point` 생성자에 제공될 수 있습니다.

여기서 실제로 일어나고 있는 것은 `Point`, `Point{Float64}` 및 `Point{Int64}`가 모두 서로 다른 생성자 함수라는 것입니다. 사실, `Point{T}`는 각 타입 `T`에 대해 별개의 생성자 함수입니다. 명시적으로 제공된 내부 생성자가 없으면, 복합 타입 `Point{T<:Real}`의 선언은 가능한 각 타입 `T<:Real`에 대해 내부 생성자 `Point{T}`를 자동으로 제공합니다. 이는 비매개변수 기본 내부 생성자가 작동하는 방식과 동일합니다. 또한, 동일한 타입의 실수 인수 쌍을 받아들이는 단일 일반 외부 `Point` 생성자를 제공합니다. 이러한 생성자의 자동 제공은 다음과 같은 명시적 선언과 동등합니다:

```jldoctest parametric2
julia> struct Point{T<:Real}
           x::T
           y::T
           Point{T}(x,y) where {T<:Real} = new(x,y)
       end

julia> Point(x::T, y::T) where {T<:Real} = Point{T}(x,y);
```

각 정의가 처리하는 생성자 호출의 형태와 같다는 점에 유의하십시오. 호출 `Point{Int64}(1,2)`는 `struct` 블록 내의 정의 `Point{T}(x,y)`를 호출합니다. 반면에 외부 생성자 선언은 동일한 실수 유형의 값 쌍에만 적용되는 일반 `Point` 생성자에 대한 메서드를 정의합니다. 이 선언은 `Point(1,2)` 및 `Point(1.0,2.5)`와 같이 명시적인 유형 매개변수 없이 생성자 호출이 작동하도록 만듭니다. 메서드 선언이 인수를 동일한 유형으로 제한하므로, 서로 다른 유형의 인수를 가진 호출 `Point(1,2.5)`는 "메서드 없음" 오류를 발생시킵니다.

우리가 `Point(1,2.5)`라는 생성자 호출이 작동하도록 하려면 정수 값 `1`을 부동 소수점 값 `1.0`으로 "승격"해야 합니다. 이를 달성하는 가장 간단한 방법은 다음과 같은 추가 외부 생성자 메서드를 정의하는 것입니다:

```jldoctest parametric2
julia> Point(x::Int64, y::Float64) = Point(convert(Float64,x),y);
```

이 방법은 [`convert`](@ref) 함수를 사용하여 `x`를 명시적으로 [`Float64`](@ref)로 변환한 다음, 두 인수가 `4d61726b646f776e2e436f64652822222c2022466c6f617436342229_40726566`인 경우에 대한 일반 생성자에게 구성을 위임합니다. 이 방법 정의로 인해 이전에는 [`MethodError`](@ref)가 이제 성공적으로 `Point{Float64}` 유형의 점을 생성합니다:

```jldoctest parametric2
julia> p = Point(1,2.5)
Point{Float64}(1.0, 2.5)

julia> typeof(p)
Point{Float64}
```

그러나 다른 유사한 호출은 여전히 작동하지 않습니다:

```jldoctest parametric2
julia> Point(1.5,2)
ERROR: MethodError: no method matching Point(::Float64, ::Int64)
The type `Point` exists, but no method is defined for this combination of argument types when trying to construct it.

Closest candidates are:
  Point(::T, !Matched::T) where T<:Real
   @ Main none:1
  Point(!Matched::Int64, !Matched::Float64)
   @ Main none:1

Stacktrace:
[...]
```

보다 일반적인 방법으로 모든 호출이 합리적으로 작동하도록 하려면 [Conversion and Promotion](@ref conversion-and-promotion)을 참조하십시오. 서스펜스를 깨뜨릴 위험을 감수하고, 모든 일반 `Point` 생성자에 대한 호출이 예상대로 작동하도록 하려면 다음과 같은 외부 메서드 정의만 있으면 된다는 것을 여기서 밝힐 수 있습니다:

```jldoctest parametric2
julia> Point(x::Real, y::Real) = Point(promote(x,y)...);
```

`promote` 함수는 모든 인수를 공통 유형으로 변환합니다. 이 경우 [`Float64`](@ref)입니다. 이 메서드 정의를 사용하면 `Point` 생성자는 [`+`](@ref)와 같은 숫자 연산자가 하는 것과 같은 방식으로 인수를 승격시키며, 모든 종류의 실수에 대해 작동합니다:

```jldoctest parametric2
julia> Point(1.5,2)
Point{Float64}(1.5, 2.0)

julia> Point(1,1//2)
Point{Rational{Int64}}(1//1, 1//2)

julia> Point(1.0,1//2)
Point{Float64}(1.0, 0.5)
```

따라서, 줄리아에서 기본적으로 제공되는 암시적 타입 매개변수 생성자는 상당히 엄격하지만, 이를 보다 느슨하면서도 합리적인 방식으로 쉽게 동작하도록 만들 수 있습니다. 게다가, 생성자는 타입 시스템, 메서드 및 다중 분기를 활용할 수 있기 때문에, 정교한 동작을 정의하는 것은 일반적으로 매우 간단합니다.

## Case Study: Rational

아마도 이러한 모든 요소를 연결하는 가장 좋은 방법은 매개변수화된 복합 유형과 그 생성자 메서드의 실제 예를 제시하는 것입니다. 이를 위해 우리는 Julia의 내장 [`Rational`](@ref) 유형과 유사한 자체 유리수 유형 `OurRational`을 구현합니다. 이 유형은 [`rational.jl`](https://github.com/JuliaLang/julia/blob/master/base/rational.jl)에 정의되어 있습니다.

```jldoctest rational
julia> struct OurRational{T<:Integer} <: Real
           num::T
           den::T
           function OurRational{T}(num::T, den::T) where T<:Integer
               if num == 0 && den == 0
                    error("invalid rational: 0//0")
               end
               num = flipsign(num, den)
               den = flipsign(den, den)
               g = gcd(num, den)
               num = div(num, g)
               den = div(den, g)
               new(num, den)
           end
       end

julia> OurRational(n::T, d::T) where {T<:Integer} = OurRational{T}(n,d)
OurRational

julia> OurRational(n::Integer, d::Integer) = OurRational(promote(n,d)...)
OurRational

julia> OurRational(n::Integer) = OurRational(n,one(n))
OurRational

julia> ⊘(n::Integer, d::Integer) = OurRational(n,d)
⊘ (generic function with 1 method)

julia> ⊘(x::OurRational, y::Integer) = x.num ⊘ (x.den*y)
⊘ (generic function with 2 methods)

julia> ⊘(x::Integer, y::OurRational) = (x*y.den) ⊘ y.num
⊘ (generic function with 3 methods)

julia> ⊘(x::Complex, y::Real) = complex(real(x) ⊘ y, imag(x) ⊘ y)
⊘ (generic function with 4 methods)

julia> ⊘(x::Real, y::Complex) = (x*y') ⊘ real(y*y')
⊘ (generic function with 5 methods)

julia> function ⊘(x::Complex, y::Complex)
           xy = x*y'
           yy = real(y*y')
           complex(real(xy) ⊘ yy, imag(xy) ⊘ yy)
       end
⊘ (generic function with 6 methods)
```

첫 번째 줄 – `struct OurRational{T<:Integer} <: Real` – 은 `OurRational`이 정수 타입의 하나의 타입 매개변수를 취하며, 그 자체가 실수 타입임을 선언합니다. 필드 선언 `num::T`와 `den::T`는 `OurRational{T}` 객체에 저장된 데이터가 타입 `T`의 정수 쌍으로, 하나는 유리수 값의 분자를 나타내고 다른 하나는 분모를 나타냄을 나타냅니다.

이제 흥미로운 일이 벌어집니다. `OurRational`은 `num`과 `den`이 모두 0이 아닌지 확인하고, 모든 유리수가 "최소 항"으로 구성되며 분모가 음수가 아닌지 보장하는 단일 내부 생성자 메서드를 가지고 있습니다. 이는 분모가 음수인 경우 분자와 분모의 부호를 먼저 뒤집음으로써 달성됩니다. 그런 다음 두 값은 최대 공약수(`gcd`는 인수의 부호와 관계없이 항상 비음수)를 사용하여 나누어집니다. 이것이 `OurRational`의 유일한 내부 생성자이기 때문에, 우리는 `OurRational` 객체가 항상 이 정규화된 형태로 구성된다는 것을 확신할 수 있습니다.

`OurRational`은 편의를 위해 여러 개의 외부 생성자 메서드를 제공합니다. 첫 번째는 분자와 분모가 동일한 유형일 때 유형 매개변수 `T`를 추론하는 "표준" 일반 생성자입니다. 두 번째는 주어진 분자와 분모 값이 서로 다른 유형일 때 적용됩니다: 이들은 공통 유형으로 승격된 후 일치하는 유형의 인수에 대한 외부 생성자에게 위임됩니다. 세 번째 외부 생성자는 정수 값을 분모로 `1`의 값을 제공하여 유리수로 변환합니다.

외부 생성자 정의에 따라, 우리는 `⊘` 연산자에 대한 여러 메서드를 정의했습니다. 이 연산자는 유리수를 작성하는 구문을 제공합니다 (예: `1 ⊘ 2`). Julia의 `Rational` 타입은 이 목적을 위해 [`//`](@ref) 연산자를 사용합니다. 이러한 정의 이전에 `⊘`는 구문만 있고 의미는 없는 완전히 정의되지 않은 연산자입니다. 이후에는 [Rational Numbers](@ref)에서 설명한 대로 작동합니다 – 그 전체 동작은 이 몇 줄로 정의됩니다. `⊘`의 중위 사용이 작동하는 이유는 Julia가 중위 연산자로 인식되는 기호 집합을 가지고 있기 때문입니다. 첫 번째이자 가장 기본적인 정의는 `a ⊘ b`가 `a`와 `b`가 정수일 때 `OurRational` 생성자를 적용하여 `OurRational`을 구성하도록 만듭니다. `⊘`의 피연산자 중 하나가 이미 유리수인 경우, 우리는 결과 비율에 대해 약간 다르게 새로운 유리수를 구성합니다; 이 동작은 실제로 정수로 유리수를 나누는 것과 동일합니다. 마지막으로, 복소 정수 값에 `⊘`를 적용하면 `Complex{<:OurRational}`의 인스턴스가 생성됩니다 – 실수와 허수 부분이 유리수인 복소수입니다:

```jldoctest rational
julia> z = (1 + 2im) ⊘ (1 - 2im);

julia> typeof(z)
Complex{OurRational{Int64}}

julia> typeof(z) <: Complex{<:OurRational}
true
```

따라서 `⊘` 연산자는 일반적으로 `OurRational`의 인스턴스를 반환하지만, 인수 중 하나라도 복소 정수인 경우에는 대신 `Complex{<:OurRational}`의 인스턴스를 반환합니다. 관심 있는 독자는 [`rational.jl`](https://github.com/JuliaLang/julia/blob/master/base/rational.jl)의 나머지를 살펴보는 것을 고려해야 합니다: 짧고, 독립적이며, 전체 기본 Julia 타입을 구현합니다.

## Outer-only constructors

우리가 보았듯이, 전형적인 매개변수형은 타입 매개변수가 알려졌을 때 호출되는 내부 생성자를 가지고 있습니다. 예를 들어, `Point{Int}`에는 적용되지만 `Point`에는 적용되지 않습니다. 선택적으로, 타입 매개변수를 자동으로 결정하는 외부 생성자를 추가할 수 있습니다. 예를 들어, `Point(1,2)` 호출로부터 `Point{Int}`를 생성하는 것입니다. 외부 생성자는 실제로 인스턴스를 만들기 위해 내부 생성자를 호출합니다. 그러나 경우에 따라 특정 타입 매개변수를 수동으로 요청할 수 없도록 내부 생성자를 제공하지 않는 것이 더 바람직할 수 있습니다.

예를 들어, 벡터와 그 합의 정확한 표현을 저장하는 타입을 정의한다고 가정해 보겠습니다:

```jldoctest
julia> struct SummedArray{T<:Number,S<:Number}
           data::Vector{T}
           sum::S
       end

julia> SummedArray(Int32[1; 2; 3], Int32(6))
SummedArray{Int32, Int32}(Int32[1, 2, 3], 6)
```

문제는 `S`가 `T`보다 더 큰 유형이 되기를 원한다는 것입니다. 그렇게 하면 정보 손실이 적은 상태에서 많은 요소를 합칠 수 있습니다. 예를 들어, `T`가 [`Int32`](@ref)일 때, `S`는 [`Int64`](@ref)가 되기를 원합니다. 따라서 사용자가 `SummedArray{Int32,Int32}` 유형의 인스턴스를 생성할 수 있는 인터페이스를 피하고자 합니다. 이를 위한 한 가지 방법은 `SummedArray`에 대한 생성자만 제공하고, `struct` 정의 블록 내에서 기본 생성자의 생성을 억제하는 것입니다:

```jldoctest
julia> struct SummedArray{T<:Number,S<:Number}
           data::Vector{T}
           sum::S
           function SummedArray(a::Vector{T}) where T
               S = widen(T)
               new{T,S}(a, sum(S, a))
           end
       end

julia> SummedArray(Int32[1; 2; 3], Int32(6))
ERROR: MethodError: no method matching SummedArray(::Vector{Int32}, ::Int32)
The type `SummedArray` exists, but no method is defined for this combination of argument types when trying to construct it.

Closest candidates are:
  SummedArray(::Vector{T}) where T
   @ Main none:4

Stacktrace:
[...]
```

이 생성자는 `SummedArray(a)` 구문에 의해 호출됩니다. `new{T,S}` 구문은 생성할 타입에 대한 매개변수를 지정할 수 있게 해줍니다. 즉, 이 호출은 `SummedArray{T,S}`를 반환합니다. `new{T,S}`는 모든 생성자 정의에서 사용할 수 있지만, 편의성을 위해 `new{}`의 매개변수는 가능할 경우 생성 중인 타입에서 자동으로 유도됩니다.

## Constructors are just callable objects

어떤 유형의 객체는 [made callable](@ref "Function-like objects") 메서드를 정의함으로써 생성될 수 있습니다. 여기에는 유형, 즉 [`Type`](@ref) 유형의 객체가 포함됩니다. 실제로 생성자는 단순히 호출 가능한 유형 객체로 간주될 수 있습니다. 예를 들어, `Bool` 및 그 다양한 슈퍼타입에 대해 정의된 많은 메서드가 있습니다:

```julia-repl
julia> methods(Bool)
# 10 methods for type constructor:
  [1] Bool(x::BigFloat)
     @ Base.MPFR mpfr.jl:393
  [2] Bool(x::Float16)
     @ Base float.jl:338
  [3] Bool(x::Rational)
     @ Base rational.jl:138
  [4] Bool(x::Real)
     @ Base float.jl:233
  [5] (dt::Type{<:Integer})(ip::Sockets.IPAddr)
     @ Sockets ~/tmp/jl/jl/julia-nightly-assert/share/julia/stdlib/v1.11/Sockets/src/IPAddr.jl:11
  [6] (::Type{T})(x::Enum{T2}) where {T<:Integer, T2<:Integer}
     @ Base.Enums Enums.jl:19
  [7] (::Type{T})(z::Complex) where T<:Real
     @ Base complex.jl:44
  [8] (::Type{T})(x::Base.TwicePrecision) where T<:Number
     @ Base twiceprecision.jl:265
  [9] (::Type{T})(x::T) where T<:Number
     @ boot.jl:894
 [10] (::Type{T})(x::AbstractChar) where T<:Union{AbstractChar, Number}
     @ char.jl:50
```

일반적인 생성자 구문은 함수와 같은 객체 구문과 정확히 동일하므로, 각 구문으로 메서드를 정의하려고 하면 첫 번째 메서드가 다음 메서드에 의해 덮어쓰여집니다:

```jldoctest
julia> struct S
           f::Int
       end

julia> S() = S(7)
S

julia> (::Type{S})() = S(8)  # overwrites the previous constructor method

julia> S()
S(8)
```
