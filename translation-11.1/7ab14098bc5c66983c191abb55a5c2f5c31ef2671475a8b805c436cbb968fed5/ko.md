# Style Guide

다음 섹션에서는 관용적인 줄리아 코딩 스타일의 몇 가지 측면을 설명합니다. 이러한 규칙은 절대적인 것이 아니며, 언어에 익숙해지고 대안 설계 중에서 선택하는 데 도움이 되는 제안일 뿐입니다.

## Indentation

4개의 공백을 들여쓰기 수준으로 사용하세요.

## Write functions, not just scripts

코드를 최상위에서 일련의 단계로 작성하는 것은 문제 해결을 시작하는 빠른 방법이지만, 가능한 한 빨리 프로그램을 함수로 나누는 것이 좋습니다. 함수는 더 재사용 가능하고 테스트 가능하며, 어떤 단계가 수행되고 있는지, 그 입력과 출력이 무엇인지 명확하게 합니다. 또한, 함수 내부의 코드는 Julia의 컴파일러 작동 방식 때문에 최상위 코드보다 훨씬 빠르게 실행되는 경향이 있습니다.

함수는 전역 변수(상수인 [`pi`](@ref)를 제외하고)에서 직접 작동하기보다는 인수를 받아야 한다는 점도 강조할 가치가 있다.

## Avoid writing overly-specific types

코드는 가능한 한 일반적이어야 합니다. 대신 다음과 같이 작성하는 것을 피하십시오:

```julia
Complex{Float64}(x)
```

사용 가능한 일반 함수를 사용하는 것이 좋습니다:

```julia
complex(float(x))
```

두 번째 버전은 항상 동일한 유형 대신 `x`를 적절한 유형으로 변환합니다.

이 스타일 포인트는 특히 함수 인수와 관련이 있습니다. 예를 들어, 인수를 `Int` 또는 [`Int32`](@ref) 유형으로 선언하지 마십시오. 실제로는 추상 유형 [`Integer`](@ref)로 표현할 수 있는 모든 정수일 수 있습니다. 사실, 많은 경우 다른 메서드 정의와의 모호성을 해소하는 데 필요하지 않는 한 인수 유형을 완전히 생략할 수 있습니다. 왜냐하면 지원하지 않는 유형이 전달되면 어차피 [`MethodError`](@ref)가 발생할 것이기 때문입니다. (이는 [duck typing](https://en.wikipedia.org/wiki/Duck_typing)로 알려져 있습니다.)

예를 들어, 다음과 같은 `addone` 함수의 정의를 고려해 보세요. 이 함수는 인수에 1을 더한 값을 반환합니다:

```julia
addone(x::Int) = x + 1                 # works only for Int
addone(x::Integer) = x + oneunit(x)    # any integer type
addone(x::Number) = x + oneunit(x)     # any numeric type
addone(x) = x + oneunit(x)             # any type supporting + and oneunit
```

`addone`의 마지막 정의는 [`oneunit`](@ref)를 지원하는 모든 유형을 처리합니다(이는 `x`와 동일한 유형으로 1을 반환하여 원하지 않는 유형 승격을 피합니다) 및 해당 인수로 [`+`](@ref) 함수를 처리합니다. 중요한 점은 *일반적인* `addone(x) = x + oneunit(x)`만 정의하는 데 *성능 저하가 없다*는 것입니다. 왜냐하면 Julia는 필요에 따라 자동으로 특수화된 버전을 컴파일하기 때문입니다. 예를 들어, `addone(12)`를 처음 호출할 때, Julia는 `x::Int` 인수에 대한 특수화된 `addone` 함수를 자동으로 컴파일하며, `oneunit`에 대한 호출은 인라인 값 `1`로 대체됩니다. 따라서 위의 `addone`에 대한 처음 세 가지 정의는 네 번째 정의와 완전히 중복됩니다.

## Handle excess argument diversity in the caller

대신:

```julia
function foo(x, y)
    x = Int(x); y = Int(y)
    ...
end
foo(x, y)
```

사용:

```julia
function foo(x::Int, y::Int)
    ...
end
foo(Int(x), Int(y))
```

이것은 더 나은 스타일입니다. 왜냐하면 `foo`는 모든 유형의 숫자를 실제로 허용하지 않기 때문입니다. 실제로는 `Int`가 필요합니다.

하나의 문제는 함수가 본질적으로 정수를 요구하는 경우, 호출자가 비정수를 어떻게 변환해야 할지 결정하도록 강제하는 것이 더 나을 수 있다는 것입니다(예: 내림 또는 올림). 또 다른 문제는 더 구체적인 유형을 선언하면 향후 메서드 정의를 위한 "공간"이 더 많이 남는다는 것입니다.

## [Append `!` to names of functions that modify their arguments](@id bang-convention)

대신:

```julia
function double(a::AbstractArray{<:Number})
    for i in eachindex(a)
        a[i] *= 2
    end
    return a
end
```

사용:

```julia
function double!(a::AbstractArray{<:Number})
    for i in eachindex(a)
        a[i] *= 2
    end
    return a
end
```

Julia Base는 이러한 규칙을 전반적으로 사용하며 복사 및 수정 형태의 함수 예제를 포함하고 있습니다(예: [`sort`](@ref) 및 [`sort!`](@ref)), 그리고 단순히 수정만 하는 다른 예제도 있습니다(예: [`push!`](@ref), [`pop!`](@ref), [`splice!`](@ref)). 이러한 함수는 편의를 위해 수정된 배열을 반환하는 것이 일반적입니다.

IO 또는 난수 생성기(RNG)를 사용하는 함수는 주목할 만한 예외입니다: 이러한 함수는 거의 항상 IO 또는 RNG를 변형해야 하므로, `!`로 끝나는 함수는 IO를 변형하거나 RNG 상태를 진행하는 것 이외의 변형을 나타내기 위해 사용됩니다. 예를 들어, `rand(x)`는 RNG를 변형하지만, `rand!(x)`는 RNG와 `x`를 모두 변형합니다; 마찬가지로, `read(io)`는 `io`를 변형하지만, `read!(io, x)`는 두 인수를 모두 변형합니다.

## Avoid strange type `Union`s

`Union{Function,AbstractString}`와 같은 유형은 종종 디자인이 더 깔끔할 수 있다는 신호입니다.

## Avoid elaborate container types

다음과 같은 배열을 구성하는 것은 보통 큰 도움이 되지 않습니다:

```julia
a = Vector{Union{Int,AbstractString,Tuple,Array}}(undef, n)
```

이 경우 `Vector{Any}(undef, n)`이 더 좋습니다. 또한 특정 사용을 주석 처리하는 것이 (예: `a[i]::Int`) 여러 대안을 하나의 유형으로 묶으려는 것보다 컴파일러에 더 도움이 됩니다.

## Prefer exported methods over direct field access

관용적인 Julia 코드는 일반적으로 모듈의 내보낸 메서드를 해당 타입의 인터페이스로 취급해야 합니다. 객체의 필드는 일반적으로 구현 세부사항으로 간주되며, 사용자 코드는 API로 명시되지 않는 한 이를 직접 접근해서는 안 됩니다. 이는 여러 가지 이점을 가지고 있습니다:

  * 패키지 개발자는 사용자 코드를 손상시키지 않고 구현을 변경할 수 있는 자유가 더 많습니다.
  * 메서드는 [`map`](@ref)와 같은 고차원 구조에 전달될 수 있습니다 (예: `map(imag, zs)` 대신 `[z.im for z in zs]`).
  * 메서드는 추상 타입에서 정의될 수 있습니다.
  * 메서드는 서로 다른 유형 간에 공유될 수 있는 개념적 작업을 설명할 수 있습니다(예: `real(z)`는 복소수 또는 쿼터니언에서 작동합니다).

줄리아의 디스패치 시스템은 이 스타일을 장려합니다. 왜냐하면 `play(x::MyType)`는 특정 타입에 대한 `play` 메서드만 정의하고, 다른 타입은 각자의 구현을 가질 수 있기 때문입니다.

유사하게, 비수출 함수는 일반적으로 내부적이며 변경될 수 있으며, 문서에서 달리 명시하지 않는 한 그렇습니다. 이름에 `_` 접두사(또는 접미사)가 붙여져 "내부" 또는 구현 세부사항임을 더욱 암시하는 경우가 있지만, 이는 규칙은 아닙니다.

이 규칙에 대한 반례로는 [`NamedTuple`](@ref), [`RegexMatch`](@ref match), [`StatStruct`](@ref stat)가 포함됩니다.

## Use naming conventions consistent with Julia `base/`

  * 모듈 및 타입 이름은 대문자와 카멜 케이스를 사용합니다: `module SparseArrays`, `struct UnitRange`.
  * 함수는 소문자입니다 ([`maximum`](@ref), [`convert`](@ref)) 그리고, 읽을 수 있을 때는 여러 단어가 함께 붙어 있습니다 ([`isequal`](@ref), [`haskey`](@ref)). 필요할 때는 단어 구분자로 언더스코어를 사용합니다. 언더스코어는 개념의 조합을 나타내는 데에도 사용됩니다 ([`remotecall_fetch`](@ref)는 `fetch(remotecall(...))`의 더 효율적인 구현으로).
  * 인수를 하나 이상 변경하는 함수는 `!`로 끝납니다.
  * 간결함은 중요하지만, 약어를 피하십시오 ([`indexin`](@ref) 대신 `indxin` 사용) 왜냐하면 특정 단어가 어떻게 약어로 사용되는지 기억하기 어려워지기 때문입니다.

함수 이름이 여러 단어로 구성되어야 하는 경우, 그것이 여러 개념을 나타낼 수 있는지 고려하고 조각으로 나누는 것이 더 나을 수 있습니다.

## Write functions with argument ordering similar to Julia Base

일반적으로 Base 라이브러리는 함수에 대한 인수의 다음과 같은 순서를 사용합니다.

1. **함수 인수**. 함수 인수를 먼저 두면 [`do`](@ref) 블록을 사용하여 다중 행 익명 함수를 전달할 수 있습니다.
2. **I/O 스트림**. `IO` 객체를 먼저 지정하면 [`sprint`](@ref)와 같은 함수에 함수를 전달할 수 있습니다. 예: `sprint(show, x)`.
3. **입력이 변형되고 있습니다**. 예를 들어, [`fill!(x, v)`](@ref fill!)에서 `x`는 변형되는 객체이며, `x`에 삽입될 값 앞에 나타납니다.
4. **유형**. 유형을 전달하는 것은 일반적으로 출력이 주어진 유형을 가질 것임을 의미합니다. [`parse(Int, "1")`](@ref parse)에서 유형은 구문 분석할 문자열 앞에 나타납니다. 유형이 먼저 나타나는 예가 많이 있지만, [`read(io, String)`](@ref read)에서는 `IO` 인수가 유형보다 먼저 나타나며, 이는 여기서 설명한 순서와 일치합니다.
5. **입력이 변형되지 않음**. `fill!(x, v)`에서 `v`는 *변형되지 않으며* `x` 다음에 옵니다.
6. **키**. 연관 컬렉션의 경우, 이는 키-값 쌍의 키입니다. 다른 인덱스 컬렉션의 경우, 이는 인덱스입니다.
7. **값**. 연관 컬렉션의 경우, 이는 키-값 쌍의 값입니다. [`fill!(x, v)`](@ref fill!)와 같은 경우, 이는 `v`입니다.
8. **모든 것 외에**. 다른 모든 주장.
9. **가변 인자**. 이는 함수 호출의 끝에 무한히 나열할 수 있는 인자를 의미합니다. 예를 들어, `Matrix{T}(undef, dims)`에서 차원은 [`Tuple`](@ref)와 같이 제공될 수 있으며, 예를 들어 `Matrix{T}(undef, (1,2))` 또는 [`Vararg`](@ref)와 같이 제공될 수 있습니다. 예를 들어 `Matrix{T}(undef, 1, 2)`와 같습니다.
10. **키워드 인수**. 줄리아에서 키워드 인수는 함수 정의에서 어차피 마지막에 와야 하므로, 완전성을 위해 여기에 나열되어 있습니다.

대부분의 함수는 위에 나열된 모든 종류의 인수를 사용하지 않습니다. 숫자는 함수에 적용 가능한 인수에 대해 사용해야 하는 우선 순위를 나타냅니다.

물론 몇 가지 예외가 있습니다. 예를 들어, [`convert`](@ref)에서는 타입이 항상 먼저 와야 합니다. [`setindex!`](@ref)에서는 값이 인덱스보다 먼저 와서 인덱스를 varargs로 제공할 수 있습니다.

API를 설계할 때, 가능한 한 이 일반적인 순서를 준수하는 것이 함수 사용자에게 보다 일관된 경험을 제공할 가능성이 높습니다.

## Don't overuse try-catch

오류를 잡는 것에 의존하기보다는 오류를 피하는 것이 더 좋다.

## Don't parenthesize conditions

줄리아에서는 `if`와 `while`의 조건 주위에 괄호를 사용할 필요가 없습니다. 작성하세요:

```julia
if a == b
```

대신:

```julia
if (a == b)
```

## Don't overuse `...`

스플라이싱 함수 인자는 중독성이 있을 수 있습니다. `[a..., b...]` 대신에 단순히 `[a; b]`를 사용하세요. 이는 이미 배열을 연결합니다. [`collect(a)`](@ref)는 `[a...]`보다 낫지만, `a`가 이미 반복 가능하기 때문에 종종 그냥 두는 것이 더 좋습니다. 배열로 변환하지 마세요.

## Ensure constructors return an instance of their own type

`T(x)` 메서드가 타입 `T`에서 호출될 때, 일반적으로 타입 T의 값을 반환할 것으로 기대됩니다. 예상치 못한 타입을 반환하는 [constructor](@ref man-constructors)를 정의하면 혼란스럽고 예측할 수 없는 동작을 초래할 수 있습니다:

```jldoctest
julia> struct Foo{T}
           x::T
       end

julia> Base.Float64(foo::Foo) = Foo(Float64(foo.x))  # Do not define methods like this

julia> Float64(Foo(3))  # Should return `Float64`
Foo{Float64}(3.0)

julia> Foo{Int}(x) = Foo{Float64}(x)  # Do not define methods like this

julia> Foo{Int}(3)  # Should return `Foo{Int}`
Foo{Float64}(3.0)
```

코드의 명확성을 유지하고 타입 일관성을 보장하기 위해, 항상 생성자가 생성해야 하는 타입의 인스턴스를 반환하도록 설계해야 합니다.

## Don't use unnecessary static parameters

함수 시그니처:

```julia
foo(x::T) where {T<:Real} = ...
```

해야 합니다:

```julia
foo(x::Real) = ...
```

대신, 특히 `T`가 함수 본문에서 사용되지 않는 경우. `T`가 사용되더라도 편리하다면 [`typeof(x)`](@ref)로 대체할 수 있습니다. 성능 차이는 없습니다. 이는 정적 매개변수에 대한 일반적인 주의가 아니라, 필요하지 않은 경우에 대한 주의입니다.

또한 컨테이너 유형은 특히 함수 호출에서 유형 매개변수가 필요할 수 있습니다. 자세한 내용은 FAQ [Avoid fields with abstract containers](@ref)를 참조하세요.

## Avoid confusion about whether something is an instance or a type

다음과 같은 정의의 집합은 혼란스럽습니다:

```julia
foo(::Type{MyType}) = ...
foo(::MyType) = foo(MyType)
```

개념이 `MyType`으로 작성될지 `MyType()`으로 작성될지를 결정하고, 그에 맞춰 일관되게 작성하세요.

선호하는 스타일은 기본적으로 인스턴스를 사용하는 것이며, 나중에 문제를 해결하는 데 필요할 경우에만 `Type{MyType}`와 관련된 메서드를 추가하는 것입니다.

유형이 사실상 열거형인 경우, 이를 단일(이상적으로는 불변 구조체 또는 원시) 유형으로 정의하고 열거형 값이 그 인스턴스가 되도록 해야 합니다. 생성자와 변환은 값이 유효한지 확인할 수 있습니다. 이 설계는 열거형을 추상 유형으로 만들고 "값"을 하위 유형으로 만드는 것보다 선호됩니다.

## Don't overuse macros

매크로가 실제로 함수가 될 수 있는 경우를 인식하세요.

[`eval`](@ref)를 매크로 내에서 호출하는 것은 특히 위험한 경고 신호입니다. 이는 매크로가 최상위에서 호출될 때만 작동함을 의미합니다. 이러한 매크로가 대신 함수로 작성된다면, 자연스럽게 필요한 런타임 값에 접근할 수 있습니다.

## Don't expose unsafe operations at the interface level

네이티브 포인터를 사용하는 타입이 있는 경우:

```julia
mutable struct NativeType
    p::Ptr{UInt8}
    ...
end
```

알겠습니다. 정의를 다음과 같이 작성하지 않겠습니다:

```julia
getindex(x::NativeType, i) = unsafe_load(x.p, i)
```

문제는 이러한 유형의 사용자가 `x[i]`를 작성할 때 이 작업이 안전하지 않다는 것을 인식하지 못하고, 그로 인해 메모리 버그에 취약해질 수 있다는 것입니다.

이러한 함수는 작업이 안전한지 확인하거나 호출자에게 경고하기 위해 이름에 `unsafe`가 포함되어야 합니다.

## Don't overload methods of base container types

다음과 같은 정의를 작성하는 것이 가능합니다:

```julia
show(io::IO, v::Vector{MyType}) = ...
```

이것은 특정 새로운 요소 유형으로 벡터를 사용자 정의하여 표시하는 것을 제공할 것입니다. 매력적이지만, 이는 피해야 합니다. 문제는 사용자가 `Vector()`와 같은 잘 알려진 유형이 특정 방식으로 동작할 것이라고 기대한다는 것이며, 그 동작을 지나치게 사용자 정의하면 작업하기가 더 어려워질 수 있습니다.

## [Avoid type piracy](@id avoid-type-piracy)

"타입 해적 행위"는 자신이 정의하지 않은 타입에 대해 Base 또는 다른 패키지의 메서드를 확장하거나 재정의하는 관행을 의미합니다. 극단적인 경우, 메서드 확장 또는 재정의로 인해 잘못된 입력이 `ccall`에 전달되면 Julia가 충돌할 수 있습니다. 타입 해적 행위는 코드에 대한 추론을 복잡하게 만들 수 있으며, 예측하고 진단하기 어려운 비호환성을 초래할 수 있습니다.

예를 들어, 모듈의 기호에 대한 곱셈을 정의하고 싶다고 가정해 보겠습니다:

```julia
module A
import Base.*
*(x::Symbol, y::Symbol) = Symbol(x,y)
end
```

문제는 이제 `Base.*`를 사용하는 다른 모듈도 이 정의를 볼 수 있다는 것입니다. `Symbol`은 Base에 정의되어 있고 다른 모듈에서 사용되기 때문에, 이는 관련 없는 코드의 동작을 예기치 않게 변경할 수 있습니다. 여기에는 다른 함수 이름을 사용하거나, 정의한 다른 유형으로 `Symbol`을 감싸는 등 여러 대안이 있습니다.

때때로, 결합된 패키지는 기능과 정의를 분리하기 위해 타입 해적질에 참여할 수 있습니다. 특히 패키지가 협력 저자에 의해 설계되었고 정의가 재사용 가능할 때 그렇습니다. 예를 들어, 한 패키지는 색상 작업에 유용한 몇 가지 타입을 제공할 수 있습니다. 다른 패키지는 이러한 타입에 대한 메서드를 정의하여 색상 공간 간의 변환을 가능하게 할 수 있습니다. 또 다른 예로는 일부 C 코드에 대한 얇은 래퍼 역할을 하는 패키지가 있을 수 있으며, 다른 패키지는 이를 해적질하여 더 높은 수준의 Julia 친화적인 API를 구현할 수 있습니다.

## Be careful with type equality

일반적으로 [`isa`](@ref) 및 [`<:`](@ref)를 사용하여 타입을 테스트하는 것이 좋으며, `==`는 사용하지 않는 것이 좋습니다. 정확한 동등성을 확인하는 것은 일반적으로 알려진 구체적인 타입(예: `T == Float64`)과 비교할 때만 의미가 있거나, 당신이 *정말, 정말* 잘 알고 있을 때만 의미가 있습니다.

## Don't write a trivial anonymous function `x->f(x)` for a named function `f`

고차 함수는 종종 익명 함수와 함께 호출되기 때문에, 이것이 바람직하거나 심지어 필요하다고 결론짓기 쉽습니다. 그러나 어떤 함수도 익명 함수로 "포장"하지 않고 직접 전달할 수 있습니다. `map(x->f(x), a)` 대신 [`map(f, a)`](@ref)를 작성하세요.

## Avoid using floats for numeric literals in generic code when possible

숫자를 처리하는 일반 코드를 작성하고, 다양한 숫자 유형 인수로 실행될 것으로 예상되는 경우, 프로모션을 통해 인수에 가능한 한 적게 영향을 미치는 숫자 유형의 리터럴을 사용해 보십시오.

예를 들어,

```jldoctest
julia> f(x) = 2.0 * x
f (generic function with 1 method)

julia> f(1//2)
1.0

julia> f(1/2)
1.0

julia> f(1)
2.0
```

동안

```jldoctest
julia> g(x) = 2 * x
g (generic function with 1 method)

julia> g(1//2)
1//1

julia> g(1/2)
1.0

julia> g(1)
2
```

보시다시피, `Int` 리터럴을 사용한 두 번째 버전은 입력 인수의 타입을 유지한 반면, 첫 번째 버전은 그렇지 않았습니다. 이는 예를 들어 `promote_type(Int, Float64) == Float64`이기 때문이며, 곱셈을 통해 승격이 발생합니다. 유사하게, [`Rational`](@ref) 리터럴은 [`Float64`](@ref) 리터럴보다 타입에 덜 파괴적이지만 `Int`보다는 더 파괴적입니다:

```jldoctest
julia> h(x) = 2//1 * x
h (generic function with 1 method)

julia> h(1//2)
1//1

julia> h(1/2)
1.0

julia> h(1)
2//1
```

따라서 가능한 경우 `Int` 리터럴을 사용하고, 리터럴 비정수 숫자에 대해서는 `Rational{Int}`를 사용하여 코드를 더 쉽게 사용할 수 있도록 하십시오.
