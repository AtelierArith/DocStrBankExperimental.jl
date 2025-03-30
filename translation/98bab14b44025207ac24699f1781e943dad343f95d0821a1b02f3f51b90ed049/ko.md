# Methods

[Functions](@ref man-functions)에서 기억하듯이, 함수는 인수의 튜플을 반환 값에 매핑하거나 적절한 값을 반환할 수 없을 경우 예외를 발생시키는 객체입니다. 동일한 개념적 함수나 작업이 서로 다른 유형의 인수에 대해 매우 다르게 구현되는 것은 일반적입니다: 두 개의 정수를 더하는 것은 두 개의 부동 소수점 숫자를 더하는 것과 매우 다르며, 이 두 가지 모두 정수와 부동 소수점 숫자를 더하는 것과는 구별됩니다. 이러한 구현의 차이에도 불구하고, 이러한 작업은 모두 "덧셈"이라는 일반 개념에 포함됩니다. 따라서 Julia에서는 이러한 동작이 모두 단일 객체인 `+` 함수에 속합니다.

여러 다른 구현을 원활하게 사용할 수 있도록 하기 위해, 함수는 한 번에 모두 정의될 필요는 없으며, 특정 인수 유형 및 개수의 조합에 대한 특정 동작을 제공함으로써 부분적으로 정의될 수 있습니다. 함수의 가능한 동작 중 하나에 대한 정의를 *메서드*라고 합니다. 지금까지 우리는 모든 유형의 인수에 적용 가능한 단일 메서드로 정의된 함수의 예만을 제시했습니다. 그러나 메서드 정의의 시그니처는 인수의 수 외에도 인수의 유형을 나타내도록 주석을 달 수 있으며, 단일 메서드 정의 이상을 제공할 수 있습니다. 함수가 특정 인수 튜플에 적용될 때, 해당 인수에 적용 가능한 가장 구체적인 메서드가 적용됩니다. 따라서 함수의 전반적인 동작은 다양한 메서드 정의의 동작의 조합입니다. 만약 이 조합이 잘 설계되어 있다면, 메서드의 구현이 매우 다를 수 있음에도 불구하고, 함수의 외부 동작은 매끄럽고 일관되게 보일 것입니다.

함수를 적용할 때 어떤 메서드를 실행할지를 선택하는 과정을 *디스패치*라고 합니다. Julia는 디스패치 프로세스가 주어진 인수의 수와 모든 인수의 유형에 따라 호출할 함수의 메서드를 선택할 수 있도록 허용합니다. 이는 전통적인 객체 지향 언어와 다르며, 이러한 언어에서는 디스패치가 첫 번째 인수에만 기반하여 발생하며, 종종 특별한 인수 구문을 가지거나 때로는 명시적으로 인수로 작성되지 않고 암시적으로 사용됩니다. [^1] 함수의 모든 인수를 사용하여 어떤 메서드를 호출해야 할지를 선택하는 것을 [multiple dispatch](https://en.wikipedia.org/wiki/Multiple_dispatch)라고 합니다. 다중 디스패치는 수학적 코드에 특히 유용하며, 여기서 연산이 다른 인수보다 "소속"된다고 인위적으로 판단하는 것은 의미가 없습니다: `x + y`에서 덧셈 연산이 `x`에 더 소속된다고 할 수 있을까요? 수학적 연산자의 구현은 일반적으로 모든 인수의 유형에 따라 달라집니다. 그러나 수학적 연산을 넘어, 다중 디스패치는 프로그램을 구조화하고 조직하는 데 강력하고 편리한 패러다임이 됩니다.

[^1]: In C++ or Java, for example, in a method call like `obj.meth(arg1,arg2)`, the object obj "receives" the method call and is implicitly passed to the method via the `this` keyword, rather than as an explicit method argument. When the current `this` object is the receiver of a method call, it can be omitted altogether, writing just `meth(arg1,arg2)`, with `this` implied as the receiving object.

!!! note
    이 장의 모든 예제는 *같은* 모듈에서 함수에 대한 메서드를 정의한다고 가정합니다. *다른* 모듈의 함수에 메서드를 추가하려면 해당 함수를 `import` 하거나 모듈 이름으로 한정된 이름을 사용해야 합니다. [namespace management](@ref namespace-management) 섹션을 참조하세요.


## Defining Methods

지금까지 우리는 예제에서 제약이 없는 인수 유형을 가진 단일 메서드만 있는 함수만 정의했습니다. 이러한 함수는 전통적인 동적 타입 언어에서처럼 작동합니다. 그럼에도 불구하고 우리는 거의 지속적으로 다중 디스패치와 메서드를 사용해왔습니다. 앞서 언급한 `+` 함수와 같은 줄리아의 표준 함수와 연산자는 인수 유형과 개수의 다양한 가능한 조합에 대한 동작을 정의하는 여러 메서드를 가지고 있습니다.

함수를 정의할 때, `::` 타입 단언 연산자를 사용하여 적용 가능한 매개변수의 유형을 선택적으로 제한할 수 있습니다. 이 연산자는 [Composite Types](@ref) 섹션에서 소개되었습니다:

```jldoctest fofxy
julia> f(x::Float64, y::Float64) = 2x + y
f (generic function with 1 method)
```

이 함수 정의는 `x`와 `y`가 모두 [`Float64`](@ref) 유형의 값인 호출에만 적용됩니다:

```jldoctest fofxy
julia> f(2.0, 3.0)
7.0
```

다른 유형의 인수에 적용하면 [`MethodError`](@ref)가 발생합니다:

```jldoctest fofxy
julia> f(2.0, 3)
ERROR: MethodError: no method matching f(::Float64, ::Int64)
The function `f` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  f(::Float64, !Matched::Float64)
   @ Main none:1

Stacktrace:
[...]

julia> f(Float32(2.0), 3.0)
ERROR: MethodError: no method matching f(::Float32, ::Float64)
The function `f` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  f(!Matched::Float64, ::Float64)
   @ Main none:1

Stacktrace:
[...]

julia> f(2.0, "3.0")
ERROR: MethodError: no method matching f(::Float64, ::String)
The function `f` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  f(::Float64, !Matched::Float64)
   @ Main none:1

Stacktrace:
[...]

julia> f("2.0", "3.0")
ERROR: MethodError: no method matching f(::String, ::String)
The function `f` exists, but no method is defined for this combination of argument types.
```

보시다시피, 인수는 반드시 [`Float64`](@ref) 유형이어야 합니다. 정수나 32비트 부동 소수점 값과 같은 다른 숫자 유형은 자동으로 64비트 부동 소수점으로 변환되지 않으며, 문자열도 숫자로 파싱되지 않습니다. `Float64`는 구체적인 유형이며, 구체적인 유형은 Julia에서 서브클래스화될 수 없기 때문에, 이러한 정의는 정확히 `Float64` 유형인 인수에만 적용될 수 있습니다. 그러나 선언된 매개변수 유형이 추상적인 더 일반적인 메서드를 작성하는 것이 유용할 수 있습니다:

```jldoctest fofxy
julia> f(x::Number, y::Number) = 2x - y
f (generic function with 2 methods)

julia> f(2.0, 3)
1.0
```

이 메서드 정의는 [`Number`](@ref)의 인스턴스인 인수 쌍에 적용됩니다. 두 인수는 동일한 유형일 필요는 없으며, 각 인수가 숫자 값이면 됩니다. 서로 다른 숫자 유형을 처리하는 문제는 표현식 `2x - y`의 산술 연산에 위임됩니다.

여러 개의 메서드를 가진 함수를 정의하려면, 단순히 서로 다른 수와 유형의 인수를 사용하여 함수를 여러 번 정의하면 됩니다. 함수에 대한 첫 번째 메서드 정의는 함수 객체를 생성하고, 이후의 메서드 정의는 기존 함수 객체에 새로운 메서드를 추가합니다. 인수의 수와 유형에 맞는 가장 구체적인 메서드 정의가 함수가 적용될 때 실행됩니다. 따라서 위의 두 메서드 정의는 추상 유형 `Number`의 모든 인스턴스 쌍에 대한 `f`의 동작을 정의하지만, [`Float64`](@ref) 값 쌍에 대해 특정한 다른 동작을 가집니다. 인수 중 하나가 64비트 부동 소수점이지만 다른 하나가 그렇지 않은 경우, `f(Float64,Float64)` 메서드는 호출할 수 없으며, 보다 일반적인 `f(Number,Number)` 메서드를 사용해야 합니다:

```jldoctest fofxy
julia> f(2.0, 3.0)
7.0

julia> f(2, 3.0)
1.0

julia> f(2.0, 3)
1.0

julia> f(2, 3)
1
```

The `2x + y` definition is only used in the first case, while the `2x - y` definition is used in the others. No automatic casting or conversion of function arguments is ever performed: all conversion in Julia is non-magical and completely explicit. [Conversion and Promotion](@ref conversion-and-promotion), however, shows how clever application of sufficiently advanced technology can be indistinguishable from magic. [^Clarke61]

비숫자 값이나 두 개보다 적거나 많은 인수의 경우, 함수 `f`는 정의되지 않으며, 이를 적용하면 여전히 [`MethodError`](@ref) 결과가 나타납니다:

```jldoctest fofxy
julia> f("foo", 3)
ERROR: MethodError: no method matching f(::String, ::Int64)
The function `f` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  f(!Matched::Number, ::Number)
   @ Main none:1
  f(!Matched::Float64, !Matched::Float64)
   @ Main none:1

Stacktrace:
[...]

julia> f()
ERROR: MethodError: no method matching f()
The function `f` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  f(!Matched::Float64, !Matched::Float64)
   @ Main none:1
  f(!Matched::Number, !Matched::Number)
   @ Main none:1

Stacktrace:
[...]
```

함수 객체를 인터랙티브 세션에 입력하면 해당 함수에 존재하는 메서드를 쉽게 확인할 수 있습니다:

```jldoctest fofxy
julia> f
f (generic function with 2 methods)
```

이 출력은 `f`가 두 개의 메소드를 가진 함수 객체임을 알려줍니다. 해당 메소드의 시그니처를 찾으려면 [`methods`](@ref) 함수를 사용하세요:

```jldoctest fofxy
julia> methods(f)
# 2 methods for generic function "f" from Main:
 [1] f(x::Float64, y::Float64)
     @ none:1
 [2] f(x::Number, y::Number)
     @ none:1
```

`f`는 두 개의 메소드를 가지고 있음을 보여줍니다. 하나는 두 개의 `Float64` 인수를 받고, 다른 하나는 `Number` 타입의 인수를 받습니다. 또한 메소드가 정의된 파일과 줄 번호를 나타냅니다: 이 메소드들은 REPL에서 정의되었기 때문에, 우리는 명시적인 줄 번호 `none:1`을 얻습니다.

타입 선언이 `::` 없이 존재하지 않는 경우, 메서드 매개변수의 타입은 기본적으로 `Any`이며, 이는 모든 값이 줄리아의 추상 타입 `Any`의 인스턴스이기 때문에 제약이 없음을 의미합니다. 따라서 다음과 같이 `f`에 대한 포괄적인 메서드를 정의할 수 있습니다:

```jldoctest fofxy
julia> f(x,y) = println("Whoa there, Nelly.")
f (generic function with 3 methods)

julia> methods(f)
# 3 methods for generic function "f" from Main:
 [1] f(x::Float64, y::Float64)
     @ none:1
 [2] f(x::Number, y::Number)
     @ none:1
 [3] f(x, y)
     @ none:1

julia> f("foo", 1)
Whoa there, Nelly.
```

이 포괄적인 정의는 매개변수 값 쌍에 대한 다른 가능한 메서드 정의보다 덜 구체적이므로, 다른 메서드 정의가 적용되지 않는 인수 쌍에 대해서만 호출됩니다.

세 번째 메서드의 시그니처에서 `x`와 `y`에 대한 타입이 지정되지 않았음을 주목하세요. 이는 `f(x::Any, y::Any)`를 표현하는 축약된 방법입니다.

비록 간단한 개념처럼 보이지만, 값의 유형에 대한 다중 디스패치는 아마도 줄리아 언어의 가장 강력하고 중심적인 기능일 것입니다. 핵심 연산은 일반적으로 수십 개의 메서드를 가지고 있습니다:

```julia-repl
julia> methods(+)
# 180 methods for generic function "+":
[1] +(x::Bool, z::Complex{Bool}) in Base at complex.jl:227
[2] +(x::Bool, y::Bool) in Base at bool.jl:89
[3] +(x::Bool) in Base at bool.jl:86
[4] +(x::Bool, y::T) where T<:AbstractFloat in Base at bool.jl:96
[5] +(x::Bool, z::Complex) in Base at complex.jl:234
[6] +(a::Float16, b::Float16) in Base at float.jl:373
[7] +(x::Float32, y::Float32) in Base at float.jl:375
[8] +(x::Float64, y::Float64) in Base at float.jl:376
[9] +(z::Complex{Bool}, x::Bool) in Base at complex.jl:228
[10] +(z::Complex{Bool}, x::Real) in Base at complex.jl:242
[11] +(x::Char, y::Integer) in Base at char.jl:40
[12] +(c::BigInt, x::BigFloat) in Base.MPFR at mpfr.jl:307
[13] +(a::BigInt, b::BigInt, c::BigInt, d::BigInt, e::BigInt) in Base.GMP at gmp.jl:392
[14] +(a::BigInt, b::BigInt, c::BigInt, d::BigInt) in Base.GMP at gmp.jl:391
[15] +(a::BigInt, b::BigInt, c::BigInt) in Base.GMP at gmp.jl:390
[16] +(x::BigInt, y::BigInt) in Base.GMP at gmp.jl:361
[17] +(x::BigInt, c::Union{UInt16, UInt32, UInt64, UInt8}) in Base.GMP at gmp.jl:398
...
[180] +(a, b, c, xs...) in Base at operators.jl:424
```

다중 디스패치와 유연한 매개변수형 시스템이 결합되어 줄리아는 구현 세부사항과 분리된 고수준 알고리즘을 추상적으로 표현할 수 있는 능력을 제공합니다.

## [Method specializations](@id man-method-specializations)

여러 개의 동일한 함수 메서드를 생성할 때, 이를 가끔 "특수화"라고 부릅니다. 이 경우, 추가 메서드를 추가하여 *함수*를 특수화하고 있습니다: 각 새로운 메서드는 함수의 새로운 특수화입니다. 위에 표시된 것처럼, 이러한 특수화는 `methods`에 의해 반환됩니다.

프로그래머의 개입 없이 발생하는 또 다른 종류의 특화가 있습니다: 줄리아의 컴파일러는 사용된 특정 인수 유형에 대해 *메서드*를 자동으로 특화할 수 있습니다. 이러한 특화는 새로운 `Method`를 생성하지 않기 때문에 `methods`에 나열되지 않지만, [`@code_typed`](@ref)와 같은 도구를 사용하면 이러한 특화를 검사할 수 있습니다.

예를 들어, 메서드를 생성하면

```
mysum(x::Real, y::Real) = x + y
```

당신은 함수 `mysum`에 하나의 새로운 메서드(아마도 유일한 메서드)를 추가했습니다. 그리고 그 메서드는 어떤 쌍의 `Real` 숫자 입력을 받습니다. 하지만 만약 당신이 그 다음에 실행한다면

```julia-repl
julia> mysum(1, 2)
3

julia> mysum(1.0, 2.0)
3.0
```

줄리아는 `mysum`을 두 번 컴파일합니다. 한 번은 `x::Int, y::Int`에 대해, 또 한 번은 `x::Float64, y::Float64`에 대해 컴파일합니다. 두 번 컴파일하는 이유는 성능 때문입니다: `mysum`이 사용하는 `+`에 대해 호출되는 메서드는 `x`와 `y`의 특정 타입에 따라 달라지며, 서로 다른 특수화를 컴파일함으로써 줄리아는 모든 메서드 조회를 미리 수행할 수 있습니다. 이렇게 하면 프로그램이 실행되는 동안 메서드 조회를 신경 쓸 필요가 없기 때문에 훨씬 더 빠르게 실행될 수 있습니다. 줄리아의 자동 특수화 기능 덕분에 일반적인 알고리즘을 작성하고 컴파일러가 필요한 각 경우를 처리하기 위해 효율적이고 특수화된 코드를 생성할 것이라고 기대할 수 있습니다.

잠재적인 전문화의 수가 사실상 무한할 수 있는 경우, Julia는 이 기본 전문화를 피할 수 있습니다. 자세한 내용은 [Be aware of when Julia avoids specializing](@ref)를 참조하세요.

## [Method Ambiguities](@id man-ambiguities)

어떤 인수 조합에 대해 고유한 가장 구체적인 메서드가 적용되지 않도록 함수 메서드 집합을 정의하는 것이 가능합니다:

```jldoctest gofxy
julia> g(x::Float64, y) = 2x + y
g (generic function with 1 method)

julia> g(x, y::Float64) = x + 2y
g (generic function with 2 methods)

julia> g(2.0, 3)
7.0

julia> g(2, 3.0)
8.0

julia> g(2.0, 3.0)
ERROR: MethodError: g(::Float64, ::Float64) is ambiguous.

Candidates:
  g(x, y::Float64)
    @ Main none:1
  g(x::Float64, y)
    @ Main none:1

Possible fix, define
  g(::Float64, ::Float64)

Stacktrace:
[...]
```

여기서 호출 `g(2.0, 3.0)`는 `g(::Float64, ::Any)` 또는 `g(::Any, ::Float64)` 메서드 중 하나로 처리될 수 있습니다. 메서드가 정의된 순서는 중요하지 않으며, 어느 쪽도 다른 쪽보다 더 구체적이지 않습니다. 이러한 경우, Julia는 임의로 메서드를 선택하는 대신 [`MethodError`](@ref)를 발생시킵니다. 교차 케이스에 대해 적절한 메서드를 지정하여 메서드 모호성을 피할 수 있습니다:

```jldoctest gofxy
julia> g(x::Float64, y::Float64) = 2x + 2y
g (generic function with 3 methods)

julia> g(2.0, 3)
7.0

julia> g(2, 3.0)
8.0

julia> g(2.0, 3.0)
10.0
```

먼저 모호성을 해소하는 방법을 정의하는 것이 권장됩니다. 그렇지 않으면 더 구체적인 방법이 정의될 때까지 일시적으로라도 모호성이 존재합니다.

더 복잡한 경우, 메서드 모호성을 해결하는 것은 특정 디자인 요소를 포함합니다; 이 주제는 [below](@ref man-method-design-ambiguities)에서 더 깊이 탐구됩니다.

## Parametric Methods

메서드 정의는 선택적으로 서명을 한정하는 타입 매개변수를 가질 수 있습니다:

```jldoctest same_typefunc
julia> same_type(x::T, y::T) where {T} = true
same_type (generic function with 1 method)

julia> same_type(x,y) = false
same_type (generic function with 2 methods)
```

첫 번째 방법은 두 인수가 동일한 구체적 유형일 때마다 적용되며, 그 유형이 무엇이든 관계없이 적용됩니다. 반면 두 번째 방법은 모든 다른 경우를 포괄하는 포괄적인 방법으로 작용합니다. 따라서 전반적으로 이는 두 인수가 동일한 유형인지 확인하는 부울 함수를 정의합니다:

```jldoctest same_typefunc
julia> same_type(1, 2)
true

julia> same_type(1, 2.0)
false

julia> same_type(1.0, 2.0)
true

julia> same_type("foo", 2.0)
false

julia> same_type("foo", "bar")
true

julia> same_type(Int32(1), Int64(2))
false
```

이러한 정의는 `UnionAll` 유형의 타입 시그니처에 해당하는 메서드와 관련이 있습니다 (참조: [UnionAll Types](@ref)).

이러한 함수 동작의 정의 방식은 줄리아에서 꽤 일반적이며, 심지어 관용적입니다. 메서드 타입 매개변수는 인수의 타입으로 사용되는 것에 제한되지 않으며, 함수의 시그니처나 본문에서 값이 사용될 수 있는 모든 곳에서 사용될 수 있습니다. 다음은 메서드 타입 매개변수 `T`가 메서드 시그니처에서 매개변수 타입 `Vector{T}`의 타입 매개변수로 사용되는 예입니다:

```jldoctest
julia> function myappend(v::Vector{T}, x::T) where {T}
           return [v..., x]
       end
myappend (generic function with 1 method)
```

타입 매개변수 `T`는 이 예제에서 추가된 요소 `x`가 벡터 `v`의 기존 eltype의 하위 유형임을 보장합니다. `where` 키워드는 메서드 시그니처 정의 후에 이러한 제약 조건 목록을 도입합니다. 이는 위에서 본 것처럼 한 줄 정의에서도 동일하게 작동하며, 아래에 설명된 대로 [return type declaration](@ref man-functions-return-type)가 있을 경우 *이전에* 나타나야 합니다.

```jldoctest
julia> (myappend(v::Vector{T}, x::T)::Vector) where {T} = [v..., x]
myappend (generic function with 1 method)

julia> myappend([1,2,3],4)
4-element Vector{Int64}:
 1
 2
 3
 4

julia> myappend([1,2,3],2.5)
ERROR: MethodError: no method matching myappend(::Vector{Int64}, ::Float64)
The function `myappend` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  myappend(::Vector{T}, !Matched::T) where T
   @ Main none:1

Stacktrace:
[...]

julia> myappend([1.0,2.0,3.0],4.0)
4-element Vector{Float64}:
 1.0
 2.0
 3.0
 4.0

julia> myappend([1.0,2.0,3.0],4)
ERROR: MethodError: no method matching myappend(::Vector{Float64}, ::Int64)
The function `myappend` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  myappend(::Vector{T}, !Matched::T) where T
   @ Main none:1

Stacktrace:
[...]
```

추가된 요소의 유형이 추가되는 벡터의 요소 유형과 일치하지 않으면 [`MethodError`](@ref)가 발생합니다. 다음 예제에서는 메서드의 유형 매개변수 `T`가 반환 값으로 사용됩니다:

```jldoctest
julia> mytypeof(x::T) where {T} = T
mytypeof (generic function with 1 method)

julia> mytypeof(1)
Int64

julia> mytypeof(1.0)
Float64
```

타입 선언에서 타입 매개변수에 서브타입 제약을 추가할 수 있는 것처럼(참조: [Parametric Types](@ref)), 메서드의 타입 매개변수에도 제약을 추가할 수 있습니다:

```jldoctest
julia> same_type_numeric(x::T, y::T) where {T<:Number} = true
same_type_numeric (generic function with 1 method)

julia> same_type_numeric(x::Number, y::Number) = false
same_type_numeric (generic function with 2 methods)

julia> same_type_numeric(1, 2)
true

julia> same_type_numeric(1, 2.0)
false

julia> same_type_numeric(1.0, 2.0)
true

julia> same_type_numeric("foo", 2.0)
ERROR: MethodError: no method matching same_type_numeric(::String, ::Float64)
The function `same_type_numeric` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  same_type_numeric(!Matched::T, ::T) where T<:Number
   @ Main none:1
  same_type_numeric(!Matched::Number, ::Number)
   @ Main none:1

Stacktrace:
[...]

julia> same_type_numeric("foo", "bar")
ERROR: MethodError: no method matching same_type_numeric(::String, ::String)
The function `same_type_numeric` exists, but no method is defined for this combination of argument types.

julia> same_type_numeric(Int32(1), Int64(2))
false
```

`same_type_numeric` 함수는 위에서 정의된 `same_type` 함수와 매우 유사하게 동작하지만, 숫자 쌍에 대해서만 정의됩니다.

매개변수 방법은 타입을 작성하는 데 사용되는 `where` 표현식과 동일한 구문을 허용합니다 (참조: [UnionAll Types](@ref)). 매개변수가 하나만 있는 경우, 중괄호(예: `where {T}`)는 생략할 수 있지만, 명확성을 위해 종종 선호됩니다. 여러 매개변수는 쉼표로 구분할 수 있으며, 예를 들어 `where {T, S<:Real}`와 같이 작성하거나 중첩된 `where`를 사용하여 `where S<:Real where T`와 같이 작성할 수 있습니다.

## Redefining Methods

메서드를 재정의하거나 새로운 메서드를 추가할 때, 이러한 변경 사항이 즉시 적용되지 않는다는 것을 인식하는 것이 중요합니다. 이는 Julia가 코드를 정적으로 추론하고 컴파일하여 빠르게 실행할 수 있는 능력의 핵심으로, 일반적인 JIT 트릭과 오버헤드 없이 가능합니다. 실제로, 새로운 메서드 정의는 현재 런타임 환경, 즉 Tasks와 Threads(그리고 이전에 정의된 `@generated` 함수들)에서 볼 수 없습니다. 이것이 의미하는 바를 보기 위해 예제를 살펴보겠습니다:

```julia-repl
julia> function tryeval()
           @eval newfun() = 1
           newfun()
       end
tryeval (generic function with 1 method)

julia> tryeval()
ERROR: MethodError: no method matching newfun()
The applicable method may be too new: running in world age xxxx1, while current world is xxxx2.
Closest candidates are:
  newfun() at none:1 (method too new to be called from this world context.)
 in tryeval() at none:1
 ...

julia> newfun()
1
```

이 예제에서 `newfun`에 대한 새로운 정의가 생성되었지만 즉시 호출할 수 없음을 관찰하십시오. 새로운 전역 변수는 `tryeval` 함수에 즉시 표시되므로 `return newfun` (괄호 없이)이라고 작성할 수 있습니다. 그러나 당신이나 당신의 호출자, 또는 그들이 호출하는 함수 등은 이 새로운 메서드 정의를 호출할 수 없습니다!

하지만 예외가 있습니다: `newfun`에 대한 향후 호출은 *REPL에서* 예상대로 작동하여 새로운 정의의 `newfun`을 보고 호출할 수 있습니다.

그러나 이후의 `tryeval` 호출은 `newfun`의 정의를 REPL의 *이전 문장에서* 보게 되며, 따라서 `tryeval` 호출 이전의 상태를 반영합니다.

당신은 이것이 어떻게 작동하는지 보기 위해 직접 시도해 볼 수 있습니다.

이 동작의 구현은 "세계 나이 카운터"입니다. 이 단조 증가 값은 각 메서드 정의 작업을 추적합니다. 이를 통해 "주어진 런타임 환경에서 볼 수 있는 메서드 정의의 집합"을 단일 숫자 또는 "세계 나이"로 설명할 수 있습니다. 또한 두 세계에서 사용 가능한 메서드를 단순히 그들의 서수 값을 비교함으로써 비교할 수 있습니다. 위의 예에서 우리는 "현재 세계"(메서드 `newfun`이 존재하는 세계)가 `tryeval`의 실행이 시작될 때 고정된 작업 로컬 "런타임 세계"보다 하나 더 크다는 것을 봅니다.

때때로 이것을 우회해야 할 필요가 있습니다(예: 위의 REPL을 구현하는 경우). 다행히도 쉬운 해결책이 있습니다: [`Base.invokelatest`](@ref) 함수를 호출하세요:

```jldoctest
julia> function tryeval2()
           @eval newfun2() = 2
           Base.invokelatest(newfun2)
       end
tryeval2 (generic function with 1 method)

julia> tryeval2()
2
```

마지막으로, 이 규칙이 적용되는 좀 더 복잡한 예제를 살펴보겠습니다. `f(x)`라는 함수를 정의하고, 처음에는 하나의 메서드가 있습니다:

```jldoctest redefinemethod
julia> f(x) = "original definition"
f (generic function with 1 method)
```

다른 연산을 시작해 보세요 `f(x)`:

```jldoctest redefinemethod
julia> g(x) = f(x)
g (generic function with 1 method)

julia> t = @async f(wait()); yield();
```

이제 `f(x)`에 몇 가지 새로운 메서드를 추가합니다:

```jldoctest redefinemethod
julia> f(x::Int) = "definition for Int"
f (generic function with 2 methods)

julia> f(x::Type{Int}) = "definition for Type{Int}"
f (generic function with 3 methods)
```

이 결과들이 어떻게 다른지 비교해 보세요:

```jldoctest redefinemethod
julia> f(1)
"definition for Int"

julia> g(1)
"definition for Int"

julia> fetch(schedule(t, 1))
"original definition"

julia> t = @async f(wait()); yield();

julia> fetch(schedule(t, 1))
"definition for Int"
```

## Design Patterns with Parametric Methods

복잡한 디스패치 로직이 성능이나 사용성에 필수적이지는 않지만, 때때로 특정 알고리즘을 표현하는 가장 좋은 방법이 될 수 있습니다. 다음은 이러한 방식으로 디스패치를 사용할 때 종종 나타나는 몇 가지 일반적인 디자인 패턴입니다.

### Extracting the type parameter from a super-type

여기 잘 정의된 요소 유형을 가진 `AbstractArray`의 임의 하위 유형에 대한 요소 유형 `T`를 반환하는 올바른 코드 템플릿이 있습니다:

```julia
abstract type AbstractArray{T, N} end
eltype(::Type{<:AbstractArray{T}}) where {T} = T
```

소위 삼각형 디스패치를 사용합니다. 예를 들어 `eltype(AbstractArray{T} where T <: Integer)`와 같은 `UnionAll` 타입은 위의 메서드와 일치하지 않습니다. `Base`에서 `eltype`의 구현은 이러한 경우를 위해 `Any`에 대한 폴백 메서드를 추가합니다.

한 가지 일반적인 실수는 반사(reflection)를 사용하여 요소 유형을 얻으려고 하는 것입니다:

```julia
eltype_wrong(::Type{A}) where {A<:AbstractArray} = A.parameters[1]
```

그러나 이것이 실패할 경우를 구성하는 것은 어렵지 않습니다:

```julia
struct BitVector <: AbstractArray{Bool, 1}; end
```

여기 우리는 매개변수가 없는 `BitVector` 유형을 생성했지만, 요소 유형은 여전히 완전히 지정되어 있으며, `T`는 `Bool`과 같습니다!

또 다른 실수는 `supertype`을 사용하여 타입 계층을 올라가려고 하는 것입니다:

```julia
eltype_wrong(::Type{AbstractArray{T}}) where {T} = T
eltype_wrong(::Type{AbstractArray{T, N}}) where {T, N} = T
eltype_wrong(::Type{A}) where {A<:AbstractArray} = eltype_wrong(supertype(A))
```

선언된 타입에는 이 방법이 작동하지만, 수퍼타입이 없는 타입에는 실패합니다:

```julia-repl
julia> eltype_wrong(Union{AbstractArray{Int}, AbstractArray{Float64}})
ERROR: MethodError: no method matching supertype(::Type{Union{AbstractArray{Float64,N} where N, AbstractArray{Int64,N} where N}})
Closest candidates are:
  supertype(::DataType) at operators.jl:43
  supertype(::UnionAll) at operators.jl:48
```

### Building a similar type with a different type parameter

일반 코드를 작성할 때, 종종 타입의 레이아웃에 약간의 변경을 가한 유사한 객체를 구성할 필요가 있으며, 이로 인해 타입 매개변수의 변경도 필요합니다. 예를 들어, 임의의 요소 타입을 가진 추상 배열이 있을 수 있으며, 특정 요소 타입으로 그 위에서 계산을 수행하고자 할 수 있습니다. 우리는 각 `AbstractArray{T}` 서브타입에 대해 이 타입 변환을 어떻게 계산할지를 설명하는 메서드를 구현해야 합니다. 서로 다른 매개변수를 가진 서브타입 간의 일반적인 변환은 존재하지 않습니다.

`AbstractArray`의 하위 유형은 일반적으로 이를 달성하기 위해 두 가지 메서드를 구현합니다: 입력 배열을 특정 `AbstractArray{T, N}` 추상 유형의 하위 유형으로 변환하는 메서드와 특정 요소 유형으로 새로 초기화되지 않은 배열을 만드는 메서드입니다. 이러한 샘플 구현은 Julia Base에서 찾을 수 있습니다. 다음은 `input`과 `output`이 동일한 유형임을 보장하는 기본 사용 예입니다:

```julia
input = convert(AbstractArray{Eltype}, input)
output = similar(input, Eltype)
```

이와 관련하여 알고리즘이 입력 배열의 복사본을 필요로 하는 경우, [`convert`](@ref)는 반환 값이 원래 입력과 별칭을 가질 수 있으므로 불충분합니다. 출력 배열을 만들기 위해 [`similar`](@ref)와 입력 데이터를 채우기 위해 [`copyto!`](@ref)를 결합하는 것은 입력 인수의 변경 가능한 복사본에 대한 요구 사항을 표현하는 일반적인 방법입니다:

```julia
copy_with_eltype(input, Eltype) = copyto!(similar(input, Eltype), input)
```

### Iterated dispatch

다단계 매개변수 인수 목록을 전송하기 위해서는 각 전송 수준을 별도의 함수로 분리하는 것이 가장 좋습니다. 이는 단일 전송 방식과 유사하게 들릴 수 있지만, 아래에서 볼 수 있듯이 여전히 더 유연합니다.

예를 들어, 배열의 요소 유형에 따라 디스패치하려고 하면 종종 모호한 상황에 직면하게 됩니다. 대신, 일반적으로 코드는 먼저 컨테이너 유형에 따라 디스패치한 다음 eltype에 따라 더 구체적인 메서드로 재귀합니다. 대부분의 경우, 알고리즘은 이러한 계층적 접근 방식에 편리하게 맞춰져 있지만, 다른 경우에는 이 엄격함을 수동으로 해결해야 합니다. 이러한 디스패치 분기는 예를 들어 두 행렬을 합산하는 논리에서 관찰할 수 있습니다:

```julia
# First dispatch selects the map algorithm for element-wise summation.
+(a::Matrix, b::Matrix) = map(+, a, b)
# Then dispatch handles each element and selects the appropriate
# common element type for the computation.
+(a, b) = +(promote(a, b)...)
# Once the elements have the same type, they can be added.
# For example, via primitive operations exposed by the processor.
+(a::Float64, b::Float64) = Core.add(a, b)
```

### Trait-based dispatch

자연스러운 확장은 위의 반복된 디스패치에 메서드 선택을 위한 레이어를 추가하여 타입 계층에 의해 정의된 집합과 독립적인 타입 집합에 대해 디스패치를 허용하는 것입니다. 우리는 문제의 타입의 `Union`을 작성하여 그러한 집합을 구성할 수 있지만, 그러면 이 집합은 생성 후 변경할 수 없는 `Union` 타입이기 때문에 확장할 수 없습니다. 그러나 이러한 확장 가능한 집합은 종종 ["Holy-trait"](https://github.com/JuliaLang/julia/issues/2345#issuecomment-54537633)라고 불리는 디자인 패턴으로 프로그래밍할 수 있습니다.

이 패턴은 함수 인수가 속할 수 있는 각 특성 집합에 대해 서로 다른 단일 값(또는 유형)을 계산하는 일반 함수를 정의하여 구현됩니다. 이 함수가 순수 함수인 경우 일반적인 디스패치와 비교하여 성능에 영향을 미치지 않습니다.

이전 섹션의 예제는 [`map`](@ref) 및 [`promote`](@ref)의 구현 세부 사항을 간과했습니다. 이 두 가지는 이러한 특성에 따라 작동합니다. `map`의 구현과 같이 행렬을 반복할 때, 데이터를 탐색하는 데 사용할 순서가 중요한 질문입니다. `AbstractArray` 하위 유형이 [`Base.IndexStyle`](@ref) 특성을 구현하면, `map`과 같은 다른 함수는 이 정보를 기반으로 최적의 알고리즘을 선택할 수 있습니다(참조: [Abstract Array Interface](@ref man-interface-array)). 이는 각 하위 유형이 `map`의 사용자 정의 버전을 구현할 필요가 없음을 의미하며, 일반 정의 + 특성 클래스가 시스템이 가장 빠른 버전을 선택할 수 있도록 합니다. 다음은 특성 기반 디스패치를 설명하는 `map`의 장난감 구현입니다:

```julia
map(f, a::AbstractArray, b::AbstractArray) = map(Base.IndexStyle(a, b), f, a, b)
# generic implementation:
map(::Base.IndexCartesian, f, a::AbstractArray, b::AbstractArray) = ...
# linear-indexing implementation (faster)
map(::Base.IndexLinear, f, a::AbstractArray, b::AbstractArray) = ...
```

이 특성 기반 접근 방식은 스칼라 `+`에 의해 사용되는 [`promote`](@ref) 메커니즘에서도 나타납니다. 이는 두 피연산자의 유형에 따라 연산을 수행하기 위한 최적의 공통 유형을 반환하는 [`promote_type`](@ref)를 사용합니다. 이를 통해 가능한 모든 유형 인수 쌍에 대해 모든 함수를 구현하는 문제를 각 유형을 공통 유형으로 변환하는 작업과 선호되는 쌍별 승격 규칙의 테이블을 구현하는 훨씬 더 작은 문제로 줄일 수 있습니다.

### Output-type computation

특성 기반 프로모션에 대한 논의는 다음 디자인 패턴으로의 전환을 제공합니다: 행렬 연산에 대한 출력 요소 유형 계산.

원시 연산을 구현하기 위해, 우리는 [`promote_type`](@ref) 함수를 사용하여 원하는 출력 유형을 계산합니다. (앞서와 같이, 우리는 `+` 호출에서 `promote` 호출이 작동하는 것을 보았습니다).

더 복잡한 행렬 함수의 경우, 더 복잡한 연산 시퀀스에 대한 예상 반환 유형을 계산해야 할 수 있습니다. 이는 종종 다음 단계에 의해 수행됩니다:

1. Write a small function `op` that expresses the set of operations performed by the kernel of the algorithm.
2. 결과 행렬의 요소 유형 `R`을 `promote_op(op, argument_types...)`로 계산합니다. 여기서 `argument_types`는 각 입력 배열에 `eltype`을 적용하여 계산됩니다.
3. `similar(R, dims)`를 사용하여 출력 행렬을 생성합니다. 여기서 `dims`는 출력 배열의 원하는 차원입니다.

보다 구체적인 예로, 일반적인 정사각형 행렬 곱셈 의사 코드는 다음과 같을 수 있습니다:

```julia
function matmul(a::AbstractMatrix, b::AbstractMatrix)
    op = (ai, bi) -> ai * bi + ai * bi

    ## this is insufficient because it assumes `one(eltype(a))` is constructable:
    # R = typeof(op(one(eltype(a)), one(eltype(b))))

    ## this fails because it assumes `a[1]` exists and is representative of all elements of the array
    # R = typeof(op(a[1], b[1]))

    ## this is incorrect because it assumes that `+` calls `promote_type`
    ## but this is not true for some types, such as Bool:
    # R = promote_type(ai, bi)

    # this is wrong, since depending on the return value
    # of type-inference is very brittle (as well as not being optimizable):
    # R = Base.return_types(op, (eltype(a), eltype(b)))

    ## but, finally, this works:
    R = promote_op(op, eltype(a), eltype(b))
    ## although sometimes it may give a larger type than desired
    ## it will always give a correct type

    output = similar(b, R, (size(a, 1), size(b, 2)))
    if size(a, 2) > 0
        for j in 1:size(b, 2)
            for i in 1:size(a, 1)
                ## here we don't use `ab = zero(R)`,
                ## since `R` might be `Any` and `zero(Any)` is not defined
                ## we also must declare `ab::R` to make the type of `ab` constant in the loop,
                ## since it is possible that typeof(a * b) != typeof(a * b + a * b) == R
                ab::R = a[i, 1] * b[1, j]
                for k in 2:size(a, 2)
                    ab += a[i, k] * b[k, j]
                end
                output[i, j] = ab
            end
        end
    end
    return output
end
```

### Separate convert and kernel logic

컴파일 시간과 테스트 복잡성을 크게 줄이는 한 가지 방법은 원하는 유형으로 변환하는 논리와 계산을 분리하는 것입니다. 이렇게 하면 컴파일러가 더 큰 커널의 나머지 본체와 독립적으로 변환 논리를 특화하고 인라인할 수 있습니다.

이것은 알고리즘에서 실제로 지원되는 특정 인수 유형으로 더 큰 유형 클래스에서 변환할 때 볼 수 있는 일반적인 패턴입니다:

```julia
complexfunction(arg::Int) = ...
complexfunction(arg::Any) = complexfunction(convert(Int, arg))

matmul(a::T, b::T) = ...
matmul(a, b) = matmul(promote(a, b)...)
```

## Parametrically-constrained Varargs methods

함수 매개변수는 "varargs" 함수([Varargs Functions](@ref))에 제공될 수 있는 인수의 수를 제한하는 데에도 사용될 수 있습니다. 이러한 제약을 나타내기 위해 `Vararg{T,N}` 표기법이 사용됩니다. 예를 들어:

```jldoctest
julia> bar(a,b,x::Vararg{Any,2}) = (a,b,x)
bar (generic function with 1 method)

julia> bar(1,2,3)
ERROR: MethodError: no method matching bar(::Int64, ::Int64, ::Int64)
The function `bar` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  bar(::Any, ::Any, ::Any, !Matched::Any)
   @ Main none:1

Stacktrace:
[...]

julia> bar(1,2,3,4)
(1, 2, (3, 4))

julia> bar(1,2,3,4,5)
ERROR: MethodError: no method matching bar(::Int64, ::Int64, ::Int64, ::Int64, ::Int64)
The function `bar` exists, but no method is defined for this combination of argument types.

Closest candidates are:
  bar(::Any, ::Any, ::Any, ::Any)
   @ Main none:1

Stacktrace:
[...]
```

더 유용하게, 매개변수에 의해 varargs 메서드를 제한하는 것이 가능합니다. 예를 들어:

```julia
function getindex(A::AbstractArray{T,N}, indices::Vararg{Number,N}) where {T,N}
```

`indices`의 수가 배열의 차원과 일치할 때만 호출됩니다.

제공된 인수의 유형만 제한해야 할 때 `Vararg{T}`는 `T...`로 동등하게 작성될 수 있습니다. 예를 들어 `f(x::Int...) = x`는 `f(x::Vararg{Int}) = x`의 약식입니다.

## Note on Optional and keyword Arguments

[Functions](@ref man-functions)에서 간략하게 언급된 바와 같이, 선택적 인자는 여러 메서드 정의에 대한 구문으로 구현됩니다. 예를 들어, 이 정의:

```julia
f(a=1,b=2) = a+2b
```

다음 세 가지 방법으로 번역됩니다:

```julia
f(a,b) = a+2b
f(a) = f(a,2)
f() = f(1,2)
```

이것은 `f()`를 호출하는 것이 `f(1,2)`를 호출하는 것과 같다는 것을 의미합니다. 이 경우 결과는 `5`입니다. 왜냐하면 `f(1,2)`가 위의 `f`의 첫 번째 메서드를 호출하기 때문입니다. 그러나 항상 그런 것은 아닙니다. 정수에 더 특화된 네 번째 메서드를 정의하면:

```julia
f(a::Int,b::Int) = a-2b
```

그렇다면 `f()`와 `f(1,2)`의 결과는 `-3`입니다. 다시 말해, 선택적 인자는 특정 함수의 메서드가 아니라 함수에 연결되어 있습니다. 어떤 메서드가 호출되는지는 선택적 인자의 유형에 따라 달라집니다. 선택적 인자가 전역 변수에 의해 정의될 때, 선택적 인자의 유형은 런타임에 변경될 수도 있습니다.

키워드 인자는 일반적인 위치 인자와는 상당히 다르게 동작합니다. 특히, 이들은 메서드 디스패치에 참여하지 않습니다. 메서드는 오직 위치 인자에 따라 디스패치되며, 키워드 인자는 일치하는 메서드가 식별된 후에 처리됩니다.

## Function-like objects

메서드는 타입과 연관되어 있으므로, 타입에 메서드를 추가함으로써 임의의 줄리아 객체를 "호출 가능"하게 만들 수 있습니다. (이러한 "호출 가능" 객체는 때때로 "펑터"라고 불립니다.)

예를 들어, 다항식의 계수를 저장하지만 다항식을 평가하는 함수처럼 동작하는 타입을 정의할 수 있습니다:

```jldoctest polynomial
julia> struct Polynomial{R}
           coeffs::Vector{R}
       end

julia> function (p::Polynomial)(x)
           v = p.coeffs[end]
           for i = (length(p.coeffs)-1):-1:1
               v = v*x + p.coeffs[i]
           end
           return v
       end

julia> (p::Polynomial)() = p(5)
```

함수가 이름이 아닌 타입으로 지정된다는 점에 유의하세요. 일반 함수와 마찬가지로 간결한 구문 형식이 있습니다. 함수 본문에서 `p`는 호출된 객체를 참조합니다. `Polynomial`은 다음과 같이 사용할 수 있습니다:

```jldoctest polynomial
julia> p = Polynomial([1,10,100])
Polynomial{Int64}([1, 10, 100])

julia> p(3)
931

julia> p()
2551
```

이 메커니즘은 또한 타입 생성자와 클로저(주변 환경을 참조하는 내부 함수)가 줄리아에서 어떻게 작동하는지를 이해하는 데 핵심입니다.

## Empty generic functions

가끔은 아직 메서드를 추가하지 않고 일반 함수를 도입하는 것이 유용합니다. 이는 인터페이스 정의와 구현을 분리하는 데 사용될 수 있습니다. 문서화나 코드 가독성을 위해서도 수행될 수 있습니다. 이를 위한 구문은 인수 튜플이 없는 빈 `function` 블록입니다:

```julia
function emptyfunc end
```

## [Method design and the avoidance of ambiguities](@id man-method-design-ambiguities)

줄리아의 메서드 다형성은 가장 강력한 기능 중 하나이지만, 이 힘을 활용하는 것은 설계상의 도전 과제를 제기할 수 있습니다. 특히, 더 복잡한 메서드 계층 구조에서는 [ambiguities](@ref man-ambiguities)가 발생하는 것이 드문 일이 아닙니다.

위에서 언급했듯이, 모호성을 해결할 수 있는 방법이 있습니다.

```julia
f(x, y::Int) = 1
f(x::Int, y) = 2
```

메서드를 정의함으로써

```julia
f(x::Int, y::Int) = 3
```

이것은 종종 올바른 전략이지만, 이 조언을 무작정 따르는 것이 역효과를 낼 수 있는 상황이 있습니다. 특히, 일반 함수가 가질 수 있는 메서드가 많을수록 모호성이 발생할 가능성이 커집니다. 메서드 계층 구조가 이 간단한 예보다 더 복잡해지면, 대안 전략에 대해 신중하게 생각해 볼 가치가 있을 수 있습니다.

아래에서는 특정 도전 과제와 이러한 문제를 해결할 수 있는 몇 가지 대안적인 방법에 대해 논의합니다.

### Tuple and NTuple arguments

`Tuple` (및 `NTuple`) 인수는 특별한 도전을 제공합니다. 예를 들어,

```julia
f(x::NTuple{N,Int}) where {N} = 1
f(x::NTuple{N,Float64}) where {N} = 2
```

`N == 0`의 가능성 때문에 모호합니다: `Int` 또는 `Float64` 변형이 호출되어야 하는지 결정할 요소가 없습니다. 모호성을 해결하기 위한 한 가지 방법은 빈 튜플에 대한 메서드를 정의하는 것입니다:

```julia
f(x::Tuple{}) = 3
```

대신, 하나의 방법을 제외하고는 튜플에 적어도 하나의 요소가 있다고 주장할 수 있습니다:

```julia
f(x::NTuple{N,Int}) where {N} = 1           # this is the fallback
f(x::Tuple{Float64, Vararg{Float64}}) = 2   # this requires at least one Float64
```

### [Orthogonalize your design](@id man-methods-orthogonalize)

두 개 이상의 인수로 디스패치하고 싶을 때, "래퍼" 함수가 더 간단한 설계를 만들 수 있는지 고려해 보세요. 예를 들어, 여러 변형을 작성하는 대신:

```julia
f(x::A, y::A) = ...
f(x::A, y::B) = ...
f(x::B, y::A) = ...
f(x::B, y::B) = ...
```

당신은 정의하는 것을 고려할 수 있습니다.

```julia
f(x::A, y::A) = ...
f(x, y) = f(g(x), g(y))
```

여기서 `g`는 인수를 타입 `A`로 변환합니다. 이는 [orthogonal design](https://en.wikipedia.org/wiki/Orthogonality_(programming))의 더 일반적인 원칙의 매우 구체적인 예입니다. 여기서 별개의 개념이 별개의 메서드에 할당됩니다. 여기서 `g`는 대부분 폴백 정의가 필요할 것입니다.

```julia
g(x::A) = x
```

관련 전략은 `promote`를 활용하여 `x`와 `y`를 공통 유형으로 가져옵니다:

```julia
f(x::T, y::T) where {T} = ...
f(x, y) = f(promote(x, y)...)
```

이 디자인의 한 가지 위험은 `x`와 `y`를 동일한 유형으로 변환하는 적절한 프로모션 방법이 없을 경우, 두 번째 방법이 무한히 자기 자신을 재귀 호출하여 스택 오버플로우를 유발할 가능성이 있다는 것입니다.

### Dispatch on one argument at a time

여러 인수에 대해 분배해야 하고, 너무 많은 조합으로 인해 모든 가능한 변형을 정의하는 것이 실용적이지 않은 경우, "이름 계단"을 도입하는 것을 고려해 보십시오. 예를 들어, 첫 번째 인수에 대해 분배한 다음 내부 메서드를 호출하는 것입니다:

```julia
f(x::A, y) = _fA(x, y)
f(x::B, y) = _fB(x, y)
```

그렇다면 내부 메서드 `_fA`와 `_fB`는 `x`와 관련하여 서로의 모호성에 대한 걱정 없이 `y`에 대해 디스패치할 수 있습니다.

이 전략에는 최소한 하나의 주요 단점이 있습니다: 많은 경우, 사용자가 내보낸 함수 `f`의 동작을 추가로 사용자 정의할 수 없습니다. 대신, 그들은 내부 메서드 `_fA`와 `_fB`에 대한 특수화를 정의해야 하며, 이는 내보낸 메서드와 내부 메서드 간의 경계를 모호하게 만듭니다.

### Abstract containers and element types

가능한 경우, 추상 컨테이너의 특정 요소 유형에 대해 디스패치하는 메서드를 정의하는 것을 피하십시오. 예를 들어,

```julia
-(A::AbstractArray{T}, b::Date) where {T<:Date}
```

방법을 정의하는 사람에게 모호성을 생성합니다.

```julia
-(A::MyArrayType{T}, b::T) where {T}
```

가장 좋은 접근 방식은 이 두 메서드 중 *어느 것도* 정의하지 않는 것입니다. 대신, 일반 메서드 `-(A::AbstractArray, b)`에 의존하고 이 메서드가 각 컨테이너 유형과 요소 유형에 대해 *별도로* 올바른 작업을 수행하는 일반 호출(예: `similar` 및 `-`)로 구현되도록 해야 합니다. 이는 [orthogonalize](@ref man-methods-orthogonalize) 귀하의 메서드에 대한 조언의 더 복잡한 변형일 뿐입니다.

이 접근 방식이 불가능할 때, 다른 개발자들과 모호성을 해결하는 방법에 대해 논의하는 것이 좋을 수 있습니다. 한 방법이 먼저 정의되었다고 해서 반드시 수정되거나 제거될 수 없다는 의미는 아닙니다. 최후의 수단으로, 한 개발자가 "임시방편" 방법을 정의할 수 있습니다.

```julia
-(A::MyArrayType{T}, b::Date) where {T<:Date} = ...
```

그것은 무식한 방법으로 모호함을 해결합니다.

### Complex method "cascades" with default arguments

"기본값"을 제공하는 "cascade"라는 메서드를 정의하는 경우, 잠재적인 기본값에 해당하는 인수를 생략하는 것에 주의해야 합니다. 예를 들어, 디지털 필터링 알고리즘을 작성하고 신호의 가장자리를 패딩을 적용하여 처리하는 메서드가 있다고 가정해 보겠습니다:

```julia
function myfilter(A, kernel, ::Replicate)
    Apadded = replicate_edges(A, size(kernel))
    myfilter(Apadded, kernel)  # now perform the "real" computation
end
```

이것은 기본 패딩을 제공하는 메서드와 충돌할 것입니다:

```julia
myfilter(A, kernel) = myfilter(A, kernel, Replicate()) # replicate the edge by default
```

이 두 방법이 함께 작동하면 `A`가 끊임없이 커지는 무한 재귀가 발생합니다.

더 나은 디자인은 호출 계층을 다음과 같이 정의하는 것입니다:

```julia
struct NoPad end  # indicate that no padding is desired, or that it's already applied

myfilter(A, kernel) = myfilter(A, kernel, Replicate())  # default boundary conditions

function myfilter(A, kernel, ::Replicate)
    Apadded = replicate_edges(A, size(kernel))
    myfilter(Apadded, kernel, NoPad())  # indicate the new boundary conditions
end

# other padding methods go here

function myfilter(A, kernel, ::NoPad)
    # Here's the "real" implementation of the core computation
end
```

`NoPad`는 다른 종류의 패딩과 동일한 인수 위치에 제공되므로, 디스패치 계층을 잘 정리하고 모호성이 발생할 가능성을 줄입니다. 또한, "공식" `myfilter` 인터페이스를 확장합니다: 패딩을 명시적으로 제어하고자 하는 사용자는 `NoPad` 변형을 직접 호출할 수 있습니다.

## Defining methods in local scope

[local scope](@ref scope-of-variables) 내에서 메서드를 정의할 수 있습니다. 예를 들어

```jldoctest
julia> function f(x)
           g(y::Int) = y + x
           g(y) = y - x
           g
       end
f (generic function with 1 method)

julia> h = f(3);

julia> h(4)
7

julia> h(4.0)
1.0
```

그러나 로컬 메서드를 조건부로 정의하거나 제어 흐름에 따라 정의해서는 *안 됩니다*, 예를 들어

```julia
function f2(inc)
    if inc
        g(x) = x + 1
    else
        g(x) = x - 1
    end
end

function f3()
    function g end
    return g
    g() = 0
end
```

정확히 어떤 함수가 정의될지 명확하지 않기 때문에, 앞으로는 이러한 방식으로 지역 메서드를 정의하는 것이 오류가 될 수 있습니다.

이런 경우에는 대신 익명 함수를 사용하세요:

```julia
function f2(inc)
    g = if inc
        x -> x + 1
    else
        x -> x - 1
    end
end
```

[^Clarke61]: Arthur C. Clarke, *Profiles of the Future* (1961): Clarke's Third Law.
