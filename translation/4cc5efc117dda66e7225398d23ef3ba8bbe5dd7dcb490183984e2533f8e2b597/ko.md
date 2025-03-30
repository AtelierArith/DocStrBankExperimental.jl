# More about types

Julia를 사용한 지 오래되었다면, 타입이 수행하는 기본적인 역할을 이해하고 있을 것입니다. 여기에서는 [Parametric Types](@ref)에 특히 초점을 맞추어 내부를 살펴보려고 합니다.

## Types and sets (and `Any` and `Union{}`/`Bottom`)

줄리아의 타입 시스템을 집합의 관점에서 이해하는 것이 가장 쉬울 수 있습니다. 프로그램이 개별 값을 조작하는 반면, 타입은 값의 집합을 나타냅니다. 이는 컬렉션과는 다릅니다. 예를 들어, [`Set`](@ref) 값의 집합은 그 자체로 단일 `Set` 값입니다. 오히려, 타입은 *가능한* 값의 집합을 설명하며, 우리가 어떤 값을 가지고 있는지에 대한 불확실성을 표현합니다.

A *concrete* type `T`는 [`typeof`](@ref) 함수에 의해 반환된 직접 태그가 `T`인 값의 집합을 설명합니다. *abstract* type은 일부 더 큰 값 집합을 설명합니다.

[`Any`](@ref)는 가능한 값의 전체 우주를 설명합니다. [`Integer`](@ref)는 `Any`의 하위 집합으로 `Int`, [`Int8`](@ref) 및 기타 구체적인 유형을 포함합니다. 내부적으로 Julia는 `Bottom`으로 알려진 또 다른 유형을 많이 사용하며, 이는 `Union{}`로도 작성할 수 있습니다. 이는 공집합에 해당합니다.

줄리아의 타입은 집합 이론의 표준 연산을 지원합니다: `T1`이 `T2`의 "부분집합" (서브타입)인지 `T1 <: T2`로 물어볼 수 있습니다. 마찬가지로, 두 타입을 교차하려면 [`typeintersect`](@ref)를 사용하고, 그들의 합집합을 [`Union`](@ref)로 취하며, 그들의 합집합을 포함하는 타입을 [`typejoin`](@ref)로 계산합니다:

```jldoctest
julia> typeintersect(Int, Float64)
Union{}

julia> Union{Int, Float64}
Union{Float64, Int64}

julia> typejoin(Int, Float64)
Real

julia> typeintersect(Signed, Union{UInt8, Int8})
Int8

julia> Union{Signed, Union{UInt8, Int8}}
Union{UInt8, Signed}

julia> typejoin(Signed, Union{UInt8, Int8})
Integer

julia> typeintersect(Tuple{Integer, Float64}, Tuple{Int, Real})
Tuple{Int64, Float64}

julia> Union{Tuple{Integer, Float64}, Tuple{Int, Real}}
Union{Tuple{Int64, Real}, Tuple{Integer, Float64}}

julia> typejoin(Tuple{Integer, Float64}, Tuple{Int, Real})
Tuple{Integer, Real}
```

이러한 연산은 추상적으로 보일 수 있지만, 줄리아의 핵심에 자리잡고 있습니다. 예를 들어, 메서드 디스패치는 메서드 목록의 항목을 순회하여 인수 튜플의 유형이 메서드 시그니처의 하위 유형인 항목에 도달할 때까지 진행됩니다. 이 알고리즘이 작동하려면 메서드가 그들의 특이성에 따라 정렬되어야 하며, 검색은 가장 특이한 메서드부터 시작해야 합니다. 따라서 줄리아는 유형에 대한 부분 순서도 구현합니다. 이는 `<:`와 유사한 기능을 통해 달성되지만, 아래에서 논의될 차이점이 있습니다.

## UnionAll types

줄리아의 타입 시스템은 또한 *반복된 유니온* 타입을 표현할 수 있습니다: 특정 변수의 모든 값에 대한 타입의 유니온입니다. 이는 일부 매개변수의 값이 알려지지 않은 경우 매개변수 타입을 설명하는 데 필요합니다.

예를 들어, [`Array`](@ref)는 `Array{Int,2}`와 같이 두 개의 매개변수를 가지고 있습니다. 요소 유형을 모른다면 `Array{T,2} where T`라고 쓸 수 있으며, 이는 모든 값 `T`에 대한 `Array{T,2}`의 합집합입니다: `Union{Array{Int8,2}, Array{Int16,2}, ...}`.

이러한 유형은 `UnionAll` 객체로 표현되며, 여기에는 변수(`T`는 이 예제에서 `TypeVar` 유형)와 래핑된 유형(`Array{T,2}`는 이 예제에서) 이 포함됩니다.

다음 방법을 고려하십시오:

```julia
f1(A::Array) = 1
f2(A::Array{Int}) = 2
f3(A::Array{T}) where {T<:Any} = 3
f4(A::Array{Any}) = 4
```

서명 - [Function calls](@ref Function-calls)에 설명된 대로 - `f3`의 타입은 튜플 타입을 감싸는 `UnionAll` 타입입니다: `Tuple{typeof(f3), Array{T}} where T`. `f4`를 제외한 모든 함수는 `a = [1,2]`로 호출할 수 있으며, `f2`를 제외한 모든 함수는 `b = Any[1,2]`로 호출할 수 있습니다.

이러한 유형을 좀 더 자세히 살펴보겠습니다:

```jldoctest
julia> dump(Array)
UnionAll
  var: TypeVar
    name: Symbol T
    lb: Union{}
    ub: Any
  body: UnionAll
    var: TypeVar
      name: Symbol N
      lb: Union{}
      ub: Any
    body: Array{T, N} <: DenseArray{T, N}
      ref::MemoryRef{T}
      size::NTuple{N, Int64}
```

이것은 `Array`가 실제로 `UnionAll` 유형의 이름임을 나타냅니다. 매개변수마다 하나의 `UnionAll` 유형이 중첩되어 있습니다. 구문 `Array{Int,2}`는 `Array{Int}{2}`와 동등합니다. 내부적으로 각 `UnionAll`은 특정 변수 값으로 한 번에 하나씩, 가장 바깥쪽부터 인스턴스화됩니다. 이는 후행 유형 매개변수를 생략하는 것에 자연스러운 의미를 부여합니다. `Array{Int}`는 `Array{Int,N} where N`과 동등한 유형을 제공합니다.

`TypeVar`는 그 자체로 타입이 아니라 `UnionAll` 타입의 구조의 일부로 간주되어야 합니다. 타입 변수는 값에 대한 하한과 상한을 가지고 있습니다(필드 `lb` 및 `ub`에서). 기호 `name`은 순전히 장식적입니다. 내부적으로 `TypeVar`는 주소에 따라 비교되므로 "다른" 타입 변수를 구별할 수 있도록 변경 가능한 타입으로 정의됩니다. 그러나 관례상 변경되어서는 안 됩니다.

`TypeVar`를 수동으로 생성할 수 있습니다:

```jldoctest
julia> TypeVar(:V, Signed, Real)
Signed<:V<:Real
```

이러한 인수 중 `name` 기호를 제외한 모든 인수를 생략할 수 있는 편리한 버전이 있습니다.

`Array{T} where T<:Integer`는 다음과 같이 낮춰집니다.

```julia
let T = TypeVar(:T,Integer)
    UnionAll(T, Array{T})
end
```

그래서 `TypeVar`를 수동으로 구성하는 것은 드물게 필요합니다(실제로, 이는 피해야 합니다).

## Free variables

*자유* 타입 변수의 개념은 타입 시스템에서 매우 중요합니다. 우리는 변수 `V`가 타입 `T`에서 자유롭다고 말하는데, 이는 `T`가 변수 `V`를 도입하는 `UnionAll`을 포함하지 않을 때를 의미합니다. 예를 들어, 타입 `Array{Array{V} where V<:Integer}`는 자유 변수가 없지만, 그 안에 있는 `Array{V}` 부분은 자유 변수 `V`를 가지고 있습니다.

자유 변수를 가진 타입은 어떤 의미에서 실제로는 타입이 아닙니다. `Array{Array{T}} where T` 타입을 고려해 보세요. 이는 모든 동종 배열의 배열을 참조합니다. 내부 타입인 `Array{T}`는 혼자서 보면 어떤 종류의 배열을 참조하는 것처럼 보일 수 있습니다. 그러나 외부 배열의 모든 요소는 *같은* 배열 타입을 가져야 하므로 `Array{T}`는 단순히 어떤 오래된 배열을 참조할 수 없습니다. `Array{T}`는 효과적으로 여러 번 "발생"한다고 말할 수 있으며, `T`는 각 "시간"마다 같은 값을 가져야 합니다.

이러한 이유로 C API의 `jl_has_free_typevars` 함수는 매우 중요합니다. 이 함수가 true를 반환하는 타입은 서브타입 및 기타 타입 함수에서 의미 있는 답변을 제공하지 않습니다.

## TypeNames

다음 두 [`Array`](@ref) 유형은 기능적으로 동등하지만 출력이 다릅니다:

```jldoctest
julia> TV, NV = TypeVar(:T), TypeVar(:N)
(T, N)

julia> Array
Array

julia> Array{TV, NV}
Array{T, N}
```

이들은 `TypeName` 유형의 객체인 `name` 필드를 검사하여 구분할 수 있습니다:

```julia-repl
julia> dump(Array{Int,1}.name)
TypeName
  name: Symbol Array
  module: Module Core
  names: empty SimpleVector
  wrapper: UnionAll
    var: TypeVar
      name: Symbol T
      lb: Union{}
      ub: Any
    body: UnionAll
      var: TypeVar
        name: Symbol N
        lb: Union{}
        ub: Any
      body: Array{T, N} <: DenseArray{T, N}
  cache: SimpleVector
    ...

  linearcache: SimpleVector
    ...

  hash: Int64 -7900426068641098781
  mt: MethodTable
    name: Symbol Array
    defs: Nothing nothing
    cache: Nothing nothing
    max_args: Int64 0
    module: Module Core
    : Int64 0
    : Int64 0
```

이 경우 관련 필드는 `wrapper`로, 새로운 `Array` 유형을 만들기 위해 사용되는 최상위 유형에 대한 참조를 보유합니다.

```julia-repl
julia> pointer_from_objref(Array)
Ptr{Cvoid} @0x00007fcc7de64850

julia> pointer_from_objref(Array.body.body.name.wrapper)
Ptr{Cvoid} @0x00007fcc7de64850

julia> pointer_from_objref(Array{TV,NV})
Ptr{Cvoid} @0x00007fcc80c4d930

julia> pointer_from_objref(Array{TV,NV}.name.wrapper)
Ptr{Cvoid} @0x00007fcc7de64850
```

[`Array`](@ref)의 `wrapper` 필드는 자신을 가리키지만, `Array{TV,NV}`는 타입의 원래 정의로 다시 가리킵니다.

다른 필드는 어떨까요? `hash`는 각 유형에 정수를 할당합니다. `cache` 필드를 살펴보려면 Array보다 덜 자주 사용되는 유형을 선택하는 것이 좋습니다. 먼저 우리만의 유형을 만들어 봅시다:

```jldoctest
julia> struct MyType{T,N} end

julia> MyType{Int,2}
MyType{Int64, 2}

julia> MyType{Float32, 5}
MyType{Float32, 5}
```

매개변수 유형을 인스턴스화할 때, 각 구체적인 유형은 유형 캐시(`MyType.body.body.name.cache`)에 저장됩니다. 그러나 자유 유형 변수를 포함하는 인스턴스는 캐시되지 않습니다.

## Tuple types

튜플 타입은 흥미로운 특별 사례를 구성합니다. `x::Tuple`과 같은 선언에서 디스패치가 작동하려면, 타입이 모든 튜플을 수용할 수 있어야 합니다. 매개변수를 확인해 봅시다:

```jldoctest
julia> Tuple
Tuple

julia> Tuple.parameters
svec(Vararg{Any})
```

다른 유형과 달리, 튜플 유형은 매개변수에서 공변적이므로 이 정의는 `Tuple`이 모든 유형의 튜플과 일치하도록 허용합니다:

```jldoctest
julia> typeintersect(Tuple, Tuple{Int,Float64})
Tuple{Int64, Float64}

julia> typeintersect(Tuple{Vararg{Any}}, Tuple{Int,Float64})
Tuple{Int64, Float64}
```

그러나 가변 인자(`Vararg`) 튜플 타입에 자유 변수가 있는 경우, 다양한 종류의 튜플을 설명할 수 있습니다:

```jldoctest
julia> typeintersect(Tuple{Vararg{T} where T}, Tuple{Int,Float64})
Tuple{Int64, Float64}

julia> typeintersect(Tuple{Vararg{T}} where T, Tuple{Int,Float64})
Union{}
```

`T`가 `Tuple` 타입에 대해 자유로울 때(즉, 그 바인딩 `UnionAll` 타입이 `Tuple` 타입 외부에 있을 때), 전체 타입에 대해 하나의 `T` 값만 작동해야 합니다. 따라서 이질적인 튜플은 일치하지 않습니다.

마지막으로, `Tuple{}`는 다르다는 점에 유의할 가치가 있습니다:

```jldoctest
julia> Tuple{}
Tuple{}

julia> Tuple{}.parameters
svec()

julia> typeintersect(Tuple{}, Tuple{Int})
Union{}
```

"기본" 튜플 타입은 무엇인가요?

```julia-repl
julia> pointer_from_objref(Tuple)
Ptr{Cvoid} @0x00007f5998a04370

julia> pointer_from_objref(Tuple{})
Ptr{Cvoid} @0x00007f5998a570d0

julia> pointer_from_objref(Tuple.name.wrapper)
Ptr{Cvoid} @0x00007f5998a04370

julia> pointer_from_objref(Tuple{}.name.wrapper)
Ptr{Cvoid} @0x00007f5998a04370
```

그래서 `Tuple == Tuple{Vararg{Any}}`는 실제로 기본 타입입니다.

## Diagonal types

`Tuple{T,T} where T` 유형을 고려해 보세요. 이 서명이 있는 메서드는 다음과 같이 보일 것입니다:

```julia
f(x::T, y::T) where {T} = ...
```

일반적인 `UnionAll` 타입의 해석에 따르면, 이 `T`는 `Any`를 포함한 모든 타입을 포함하므로 이 타입은 `Tuple{Any,Any}`와 동등해야 합니다. 그러나 이 해석은 몇 가지 실질적인 문제를 일으킵니다.

먼저, `T`의 값이 메서드 정의 내에서 사용 가능해야 합니다. `f(1, 1.0)`과 같은 호출에서는 `T`가 무엇인지 명확하지 않습니다. `Union{Int,Float64}`일 수도 있고, 아마도 [`Real`](@ref)일 수도 있습니다. 직관적으로, 우리는 선언 `x::T`가 `T === typeof(x)`를 의미한다고 기대합니다. 이 불변성이 유지되도록 하려면, 이 메서드 내에서 `typeof(x) === typeof(y) === T`가 되어야 합니다. 이는 메서드가 정확히 같은 타입의 인수에 대해서만 호출되어야 함을 의미합니다.

두 값이 동일한 유형인지 여부에 따라 분기할 수 있는 것이 매우 유용하다는 것이 밝혀졌습니다(예를 들어, 이는 승격 시스템에서 사용됩니다). 따라서 `Tuple{T,T} where T`에 대한 다른 해석을 원할 여러 가지 이유가 있습니다. 이를 작동하게 하려면 서브타입에 다음 규칙을 추가합니다: 변수가 공변 위치에서 두 번 이상 발생하면 구체적인 유형만을 범위로 제한됩니다. ("공변 위치"는 변수가 발생하는 위치와 이를 도입하는 `UnionAll` 유형 사이에 오직 `Tuple` 및 `Union` 유형만이 존재함을 의미합니다.) 이러한 변수를 "대각선 변수" 또는 "구체적 변수"라고 합니다.

예를 들어, `Tuple{T,T} where T`는 `Union{Tuple{Int8,Int8}, Tuple{Int16,Int16}, ...}`로 볼 수 있으며, 여기서 `T`는 모든 구체적인 타입을 포함합니다. 이는 흥미로운 서브타입 결과를 초래합니다. 예를 들어, `Tuple{Real,Real}`는 `Tuple{T,T} where T`의 서브타입이 아닙니다. 왜냐하면 `Tuple{Int8,Int16}`와 같이 두 요소의 타입이 다른 타입을 포함하기 때문입니다. `Tuple{Real,Real}`과 `Tuple{T,T} where T`는 비자명한 교차점 `Tuple{T,T} where T<:Real`을 가지고 있습니다. 그러나 `Tuple{Real}`은 `Tuple{T} where T`의 서브타입입니다. 왜냐하면 이 경우 `T`는 한 번만 나타나므로 대각선이 아니기 때문입니다.

다음으로 다음과 같은 서명을 고려해 보십시오:

```julia
f(a::Array{T}, x::T, y::T) where {T} = ...
```

이 경우, `T`는 `Array{T}` 내부에서 불변 위치에 발생합니다. 이는 전달되는 배열의 유형이 `T`의 값을 명확하게 결정한다는 것을 의미합니다. 우리는 `T`가 *동등성 제약*을 가지고 있다고 말합니다. 따라서 이 경우 대각선 규칙은 실제로 필요하지 않으며, 배열이 `T`를 결정하므로 `x`와 `y`는 `T`의 모든 하위 유형일 수 있습니다. 따라서 불변 위치에 발생하는 변수는 결코 대각선으로 간주되지 않습니다. 이러한 동작 선택은 약간 논란의 여지가 있습니다. 일부는 이 정의가 다음과 같이 작성되어야 한다고 생각합니다.

```julia
f(a::Array{T}, x::S, y::S) where {T, S<:T} = ...
```

`x`와 `y`가 동일한 타입을 가져야 하는지 명확히 하기 위해. 이 서명 버전에서는 그렇고, `x`와 `y`가 서로 다른 타입을 가질 수 있다면 `y`의 타입을 위한 세 번째 변수를 도입할 수 있습니다.

다음 합병증은 유니온과 대각선 변수의 상호작용입니다. 예:

```julia
f(x::Union{Nothing,T}, y::T) where {T} = ...
```

이 선언이 의미하는 바를 고려해 보십시오. `y`는 타입 `T`를 가집니다. 그러면 `x`는 동일한 타입 `T`를 가질 수도 있고, 아니면 타입 [`Nothing`](@ref)일 수도 있습니다. 따라서 다음의 모든 호출은 일치해야 합니다:

```julia
f(1, 1)
f("", "")
f(2.0, 2.0)
f(nothing, 1)
f(nothing, "")
f(nothing, 2.0)
```

이 예제들은 우리에게 무언가를 말해줍니다: `x`가 `nothing::Nothing`일 때, `y`에 대한 추가 제약이 없습니다. 마치 메서드 시그니처에 `y::Any`가 있는 것과 같습니다. 실제로, 우리는 다음과 같은 타입 동등성을 가지고 있습니다:

```julia
(Tuple{Union{Nothing,T},T} where T) == Union{Tuple{Nothing,Any}, Tuple{T,T} where T}
```

일반적인 규칙은 공변 위치에 있는 구체적인 변수가 서브타이핑 알고리즘이 그것을 한 번만 *사용*할 경우 구체적이지 않은 것처럼 작용한다는 것입니다. `x`의 타입이 `Nothing`일 때, 우리는 `Union{Nothing,T}`에서 `T`를 사용할 필요가 없습니다; 우리는 그것을 두 번째 슬롯에서만 사용합니다. 이는 `Tuple{T} where T`에서 `T`를 구체적인 타입으로 제한하는 것이 아무런 차이를 만들지 않는다는 관찰에서 자연스럽게 발생합니다; 두 경우 모두 타입은 `Tuple{Any}`와 같습니다.

그러나 *불변* 위치에 나타나는 것은 변수가 사용되든 사용되지 않든 변수를 구체적으로 만들 수 없게 합니다. 그렇지 않으면 타입은 비교되는 다른 타입에 따라 다르게 동작할 수 있어 서브타이핑이 전이적이지 않게 됩니다. 예를 들어, 다음을 고려하십시오.

```julia
Tuple{Int,Int8,Vector{Integer}} <: Tuple{T,T,Vector{Union{Integer,T}}} where T
```

`T`가 `Union` 내에서 무시된다면, `T`는 구체적이며 답은 "false"입니다. 왜냐하면 처음 두 타입이 같지 않기 때문입니다. 하지만 대신 고려해 보십시오.

```julia
Tuple{Int,Int8,Vector{Any}} <: Tuple{T,T,Vector{Union{Integer,T}}} where T
```

이제 우리는 `Union`에서 `T`를 무시할 수 없으므로(`T == Any`여야 함), `T`는 구체적이지 않으며 답은 "true"입니다. 이는 `T`의 구체성이 다른 타입에 의존하게 만들며, 이는 허용되지 않습니다. 타입은 스스로 명확한 의미를 가져야 하기 때문입니다. 따라서 `Vector` 내부의 `T`의 출현은 두 경우 모두 고려됩니다.

## Subtyping diagonal variables

대각선 변수를 위한 서브타이핑 알고리즘은 두 가지 구성 요소로 이루어져 있습니다: (1) 변수 발생 식별, (2) 대각선 변수가 구체적인 타입만을 범위로 하도록 보장하기.

첫 번째 작업은 환경의 각 변수에 대해 `occurs_inv` 및 `occurs_cov` 카운터( `src/subtype.c`에 있음)를 유지하여 불변 및 공변 발생의 수를 추적하는 것입니다. 변수가 대각선일 때는 `occurs_inv == 0 && occurs_cov > 1`입니다.

두 번째 작업은 변수의 하한에 조건을 부과함으로써 수행됩니다. 서브타입 알고리즘이 실행되는 동안 각 변수의 경계를 좁히며(하한을 높이고 상한을 낮추어) 서브타입 관계가 유지될 수 있는 변수 값의 범위를 추적합니다. 대각선 변수가 있는 `UnionAll` 타입의 본체 평가가 끝나면 경계의 최종 값을 살펴봅니다. 변수가 구체적이어야 하므로, 하한이 구체적 타입의 서브타입이 될 수 없다면 모순이 발생합니다. 예를 들어, [`AbstractArray`](@ref)와 같은 추상 타입은 구체적 타입의 서브타입이 될 수 없지만, `Int`와 같은 구체적 타입은 될 수 있으며, 빈 타입인 `Bottom`도 마찬가지입니다. 하한이 이 테스트를 통과하지 못하면 알고리즘은 `false`라는 답변으로 중단됩니다.

예를 들어, 문제 `Tuple{Int,String} <: Tuple{T,T} where T`에서, `T`가 `Union{Int,String}`의 슈퍼타입이라면 이것이 참이 될 것이라고 유도합니다. 그러나 `Union{Int,String}`는 추상 타입이므로, 이 관계는 성립하지 않습니다.

이 구체성 테스트는 함수 `is_leaf_bound`에 의해 수행됩니다. 이 테스트는 `jl_is_leaf_type`와 약간 다르며, `Bottom`에 대해서도 `true`를 반환합니다. 현재 이 함수는 휴리스틱이며 모든 가능한 구체적 유형을 포착하지는 않습니다. 하한이 구체적인지 여부는 다른 유형 변수의 경계 값에 따라 달라질 수 있기 때문에 어려움이 있습니다. 예를 들어, `Vector{T}`는 `T`의 상한과 하한이 모두 `Int`일 때만 구체적 유형 `Vector{Int}`와 동등합니다. 우리는 아직 이를 위한 완전한 알고리즘을 개발하지 않았습니다.

## Introduction to the internal machinery

대부분의 타입 관련 작업은 `jltypes.c`와 `subtype.c` 파일에서 찾을 수 있습니다. 시작하는 좋은 방법은 서브타이핑이 작동하는 모습을 보는 것입니다. `make debug`로 Julia를 빌드하고 디버거 내에서 Julia를 실행하세요. [gdb debugging tips](@ref gdb-debugging-tips)에는 유용할 수 있는 몇 가지 팁이 있습니다.

REPL 자체에서 서브타이핑 코드가 많이 사용되기 때문에 – 따라서 이 코드의 중단점이 자주 발생하므로 – 다음 정의를 만드는 것이 가장 쉽습니다:

```julia-repl
julia> function mysubtype(a,b)
           ccall(:jl_breakpoint, Cvoid, (Any,), nothing)
           a <: b
       end
```

그런 다음 `jl_breakpoint`에서 중단점을 설정합니다. 이 중단점이 트리거되면 다른 함수에서 중단점을 설정할 수 있습니다.

워밍업으로 다음을 시도해 보세요:

```julia
mysubtype(Tuple{Int, Float64}, Tuple{Integer, Real})
```

우리는 더 복잡한 사례를 시도함으로써 더 흥미롭게 만들 수 있습니다:

```julia
mysubtype(Tuple{Array{Int,2}, Int8}, Tuple{Array{T}, T} where T)
```

## Subtyping and method sorting

`type_morespecific` 함수는 메서드 테이블에서 함수에 대한 부분 순서를 부여하는 데 사용됩니다 (가장 구체적인 것에서 가장 덜 구체적인 것까지). 구체성은 엄격합니다; 만약 `a`가 `b`보다 더 구체적이라면, `a`는 `b`와 같지 않으며 `b`는 `a`보다 더 구체적이지 않습니다.

`a`가 `b`의 엄격한 하위 유형이라면, 자동으로 더 구체적인 것으로 간주됩니다. 거기에서 `type_morespecific`는 덜 공식적인 규칙을 사용합니다. 예를 들어, `subtype`은 인수의 수에 민감하지만, `type_morespecific`는 그럴 필요가 없을 수 있습니다. 특히, `Tuple{Int,AbstractFloat}`는 `Tuple{Integer}`보다 더 구체적이지만, 하위 유형은 아닙니다. (`Tuple{Int,AbstractFloat}`와 `Tuple{Integer,Float64}` 중 어느 것도 서로보다 더 구체적이지 않습니다.) 마찬가지로, `Tuple{Int,Vararg{Int}}`는 `Tuple{Integer}`의 하위 유형이 아니지만, 더 구체적인 것으로 간주됩니다. 그러나 `morespecific`는 길이에 대해 보너스를 받습니다: 특히, `Tuple{Int,Int}`는 `Tuple{Int,Vararg{Int}}`보다 더 구체적입니다.

메서드가 어떻게 정렬되는지 디버깅하는 경우, 함수를 정의하는 것이 편리할 수 있습니다:

```julia
type_morespecific(a, b) = ccall(:jl_type_morespecific, Cint, (Any,Any), a, b)
```

튜플 타입 `a`가 튜플 타입 `b`보다 더 구체적인지 테스트할 수 있게 해줍니다.
