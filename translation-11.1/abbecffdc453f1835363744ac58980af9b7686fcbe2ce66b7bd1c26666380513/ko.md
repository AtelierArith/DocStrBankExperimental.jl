# Interfaces

줄리아의 많은 힘과 확장성은 비공식 인터페이스 모음에서 비롯됩니다. 특정 메서드를 사용자 정의 유형에 맞게 확장함으로써, 해당 유형의 객체는 이러한 기능을 받을 뿐만 아니라, 이러한 동작을 일반적으로 기반으로 작성된 다른 메서드에서도 사용될 수 있습니다.

## [Iteration](@id man-interface-iteration)

항상 필요한 두 가지 방법이 있습니다:

| Required method         | Brief description                                                                        |
|:----------------------- |:---------------------------------------------------------------------------------------- |
| [`iterate(iter)`](@ref) | Returns either a tuple of the first item and initial state or [`nothing`](@ref) if empty |
| `iterate(iter, state)`  | Returns either a tuple of the next item and next state or `nothing` if no items remain   |

어떤 상황에서는 정의해야 할 몇 가지 추가 메서드가 있습니다. 항상 `Base.IteratorSize(IterType)`와 `length(iter)` 중 적어도 하나는 정의해야 한다는 점에 유의하세요. `Base.IteratorSize(IterType)`의 기본 정의는 `Base.HasLength()`입니다.

| Method                                  | When should this method be defined?                                         | Default definition | Brief description                                                                                                                                                                                        |
|:--------------------------------------- |:--------------------------------------------------------------------------- |:------------------ |:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [`Base.IteratorSize(IterType)`](@ref)   | If default is not appropriate                                               | `Base.HasLength()` | One of `Base.HasLength()`, `Base.HasShape{N}()`, `Base.IsInfinite()`, or `Base.SizeUnknown()` as appropriate                                                                                             |
| [`length(iter)`](@ref)                  | If `Base.IteratorSize()` returns `Base.HasLength()` or `Base.HasShape{N}()` | (*undefined*)      | The number of items, if known                                                                                                                                                                            |
| [`size(iter, [dim])`](@ref)             | If `Base.IteratorSize()` returns `Base.HasShape{N}()`                       | (*undefined*)      | The number of items in each dimension, if known                                                                                                                                                          |
| [`Base.IteratorEltype(IterType)`](@ref) | If default is not appropriate                                               | `Base.HasEltype()` | Either `Base.EltypeUnknown()` or `Base.HasEltype()` as appropriate                                                                                                                                       |
| [`eltype(IterType)`](@ref)              | If default is not appropriate                                               | `Any`              | The type of the first entry of the tuple returned by `iterate()`                                                                                                                                         |
| [`Base.isdone(iter, [state])`](@ref)    | **Must** be defined if iterator is stateful                                 | `missing`          | Fast-path hint for iterator completion. If not defined for a stateful iterator then functions that check for done-ness, like `isempty()` and `zip()`, may mutate the iterator and cause buggy behaviour! |

순차 반복은 [`iterate`](@ref) 함수에 의해 구현됩니다. 반복되는 객체를 변형하는 대신, 줄리아 반복자는 객체 외부에서 반복 상태를 추적할 수 있습니다. iterate의 반환 값은 항상 값과 상태의 튜플이거나, 더 이상 요소가 남아 있지 않으면 `nothing`입니다. 상태 객체는 다음 반복에서 iterate 함수로 다시 전달되며, 일반적으로 반복 가능한 객체에 대해 비공식적인 구현 세부 사항으로 간주됩니다.

어떤 객체가 이 함수를 정의하면 반복 가능하며 [many functions that rely upon iteration](@ref lib-collections-iteration)에서 사용할 수 있습니다. 또한 구문이 다음과 같기 때문에 [`for`](@ref) 루프에서 직접 사용할 수도 있습니다:

```julia
for item in iter   # or  "for item = iter"
    # body
end
```

is translated into:

```julia
next = iterate(iter)
while next !== nothing
    (item, state) = next
    # body
    next = iterate(iter, state)
end
```

정의된 길이를 가진 제곱수의 반복 가능한 시퀀스의 간단한 예입니다:

```jldoctest squaretype
julia> struct Squares
           count::Int
       end

julia> Base.iterate(S::Squares, state=1) = state > S.count ? nothing : (state*state, state+1)
```

[`iterate`](@ref) 정의만으로도 `Squares` 타입은 이미 꽤 강력합니다. 우리는 모든 요소를 반복할 수 있습니다:

```jldoctest squaretype
julia> for item in Squares(7)
           println(item)
       end
1
4
9
16
25
36
49
```

우리는 [`in`](@ref) 또는 [`sum`](@ref)와 같이 반복 가능한 객체와 함께 작동하는 많은 내장 메서드를 사용할 수 있습니다:

```jldoctest squaretype
julia> 25 in Squares(10)
true

julia> sum(Squares(100))
338350
```

이 반복 가능한 컬렉션에 대해 Julia에게 더 많은 정보를 제공하기 위해 확장할 수 있는 몇 가지 방법이 있습니다. `Squares` 시퀀스의 요소는 항상 `Int`임을 알고 있습니다. [`eltype`](@ref) 메서드를 확장함으로써, 우리는 Julia에게 그 정보를 제공하고 더 복잡한 메서드에서 더 전문화된 코드를 생성하는 데 도움을 줄 수 있습니다. 또한, 시퀀스의 요소 수를 알고 있으므로 [`length`](@ref)도 확장할 수 있습니다.

```jldoctest squaretype
julia> Base.eltype(::Type{Squares}) = Int # Note that this is defined for the type

julia> Base.length(S::Squares) = S.count
```

이제 우리가 줄리아에게 [`collect`](@ref) 모든 요소를 배열로 요청하면, 단순히 [`push!`](@ref) 각 요소를 `Vector{Any}`에 추가하는 대신 올바른 크기의 `Vector{Int}`를 미리 할당할 수 있습니다:

```jldoctest squaretype
julia> collect(Squares(4))
4-element Vector{Int64}:
  1
  4
  9
 16
```

우리는 일반적인 구현에 의존할 수 있지만, 더 간단한 알고리즘이 있다는 것을 아는 특정 메서드를 확장할 수도 있습니다. 예를 들어, 제곱의 합을 계산하는 공식이 있으므로, 일반적인 반복 버전을 더 성능이 좋은 솔루션으로 재정의할 수 있습니다:

```jldoctest squaretype
julia> Base.sum(S::Squares) = (n = S.count; return n*(n+1)*(2n+1)÷6)

julia> sum(Squares(1803))
1955361914
```

이것은 Julia Base 전반에 걸쳐 매우 일반적인 패턴입니다: 소수의 필수 메서드가 비공식 인터페이스를 정의하여 더 많은 고급 동작을 가능하게 합니다. 경우에 따라, 타입은 특정 경우에 더 효율적인 알고리즘을 사용할 수 있을 때 추가적인 동작을 전문화하고자 할 것입니다.

컬렉션을 *역순*으로 반복할 수 있도록 하는 것도 종종 유용합니다. [`Iterators.reverse(iterator)`](@ref)를 반복함으로써 가능합니다. 그러나 실제로 역순 반복을 지원하려면, 반복자 유형 `T`가 `Iterators.Reverse{T}`에 대해 `iterate`를 구현해야 합니다. (주어진 `r::Iterators.Reverse{T}`에서, 기본 반복자 유형 `T`는 `r.itr`입니다.) 우리의 `Squares` 예제에서는 `Iterators.Reverse{Squares}` 메서드를 구현할 것입니다:

```jldoctest squaretype
julia> Base.iterate(rS::Iterators.Reverse{Squares}, state=rS.itr.count) = state < 1 ? nothing : (state*state, state-1)

julia> collect(Iterators.reverse(Squares(4)))
4-element Vector{Int64}:
 16
  9
  4
  1
```

## Indexing

| Methods to implement | Brief description                                             |
|:-------------------- |:------------------------------------------------------------- |
| `getindex(X, i)`     | `X[i]`, indexed access, non-scalar `i` should allocate a copy |
| `setindex!(X, v, i)` | `X[i] = v`, indexed assignment                                |
| `firstindex(X)`      | The first index, used in `X[begin]`                           |
| `lastindex(X)`       | The last index, used in `X[end]`                              |

For the `Squares` iterable above, we can easily compute the `i`th element of the sequence by squaring it.  We can expose this as an indexing expression `S[i]`. To opt into this behavior, `Squares` simply needs to define [`getindex`](@ref):

```jldoctest squaretype
julia> function Base.getindex(S::Squares, i::Int)
           1 <= i <= S.count || throw(BoundsError(S, i))
           return i*i
       end

julia> Squares(100)[23]
529
```

또한, 구문 `S[begin]` 및 `S[end]`를 지원하기 위해 [`firstindex`](@ref) 및 [`lastindex`](@ref)를 정의하여 각각 첫 번째 및 마지막 유효 인덱스를 지정해야 합니다:

```jldoctest squaretype
julia> Base.firstindex(S::Squares) = 1

julia> Base.lastindex(S::Squares) = length(S)

julia> Squares(23)[end]
529
```

다차원 `begin`/`end` 인덱싱을 위해 `a[3, begin, 7]`와 같은 예에서, `firstindex(a, dim)` 및 `lastindex(a, dim)`을 정의해야 합니다(기본적으로 각각 `axes(a, dim)`에서 `first` 및 `last`를 호출합니다).

그러나 위의 내용은 [`getindex`](@ref)를 하나의 정수 인덱스만으로 정의한다는 점에 유의해야 합니다. `Int` 이외의 다른 것으로 인덱싱하면 [`MethodError`](@ref)가 발생하여 일치하는 메서드가 없다는 오류가 발생합니다. 범위나 `Int` 벡터로 인덱싱을 지원하기 위해서는 별도의 메서드를 작성해야 합니다:

```jldoctest squaretype
julia> Base.getindex(S::Squares, i::Number) = S[convert(Int, i)]

julia> Base.getindex(S::Squares, I) = [S[i] for i in I]

julia> Squares(10)[[3,4.,5]]
3-element Vector{Int64}:
  9
 16
 25
```

이제 [indexing operations supported by some of the builtin types](@ref man-array-indexing)를 더 많이 지원하기 시작했지만, 여전히 누락된 동작이 상당수 있습니다. 이 `Squares` 시퀀스는 동작을 추가함에 따라 점점 더 벡터처럼 보이기 시작했습니다. 이러한 모든 동작을 직접 정의하는 대신, 이를 [`AbstractArray`](@ref)의 하위 유형으로 공식적으로 정의할 수 있습니다.

## [Abstract Arrays](@id man-interface-array)

| Methods to implement                     |                                        | Brief description                                                                                                                                                |
|:---------------------------------------- |:-------------------------------------- |:---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `size(A)`                                |                                        | Returns a tuple containing the dimensions of `A`                                                                                                                 |
| `getindex(A, i::Int)`                    |                                        | (if `IndexLinear`) Linear scalar indexing                                                                                                                        |
| `getindex(A, I::Vararg{Int, N})`         |                                        | (if `IndexCartesian`, where `N = ndims(A)`) N-dimensional scalar indexing                                                                                        |
| **Optional methods**                     | **Default definition**                 | **Brief description**                                                                                                                                            |
| `IndexStyle(::Type)`                     | `IndexCartesian()`                     | Returns either `IndexLinear()` or `IndexCartesian()`. See the description below.                                                                                 |
| `setindex!(A, v, i::Int)`                |                                        | (if `IndexLinear`) Scalar indexed assignment                                                                                                                     |
| `setindex!(A, v, I::Vararg{Int, N})`     |                                        | (if `IndexCartesian`, where `N = ndims(A)`) N-dimensional scalar indexed assignment                                                                              |
| `getindex(A, I...)`                      | defined in terms of scalar `getindex`  | [Multidimensional and nonscalar indexing](@ref man-array-indexing)                                                                                               |
| `setindex!(A, X, I...)`                  | defined in terms of scalar `setindex!` | [Multidimensional and nonscalar indexed assignment](@ref man-array-indexing)                                                                                     |
| `iterate`                                | defined in terms of scalar `getindex`  | Iteration                                                                                                                                                        |
| `length(A)`                              | `prod(size(A))`                        | Number of elements                                                                                                                                               |
| `similar(A)`                             | `similar(A, eltype(A), size(A))`       | Return a mutable array with the same shape and element type                                                                                                      |
| `similar(A, ::Type{S})`                  | `similar(A, S, size(A))`               | Return a mutable array with the same shape and the specified element type                                                                                        |
| `similar(A, dims::Dims)`                 | `similar(A, eltype(A), dims)`          | Return a mutable array with the same element type and size *dims*                                                                                                |
| `similar(A, ::Type{S}, dims::Dims)`      | `Array{S}(undef, dims)`                | Return a mutable array with the specified element type and size                                                                                                  |
| **Non-traditional indices**              | **Default definition**                 | **Brief description**                                                                                                                                            |
| `axes(A)`                                | `map(OneTo, size(A))`                  | Return a tuple of `AbstractUnitRange{<:Integer}` of valid indices. The axes should be their own axes, that is `axes.(axes(A),1) == axes(A)` should be satisfied. |
| `similar(A, ::Type{S}, inds)`            | `similar(A, S, Base.to_shape(inds))`   | Return a mutable array with the specified indices `inds` (see below)                                                                                             |
| `similar(T::Union{Type,Function}, inds)` | `T(Base.to_shape(inds))`               | Return an array similar to `T` with the specified indices `inds` (see below)                                                                                     |

`AbstractArray`의 하위 유형으로 정의된 경우, 단일 요소 접근 위에 구축된 반복 및 다차원 인덱싱을 포함하여 매우 방대한 세트의 풍부한 동작을 상속받습니다. 지원되는 더 많은 메서드는 [arrays manual page](@ref man-multi-dim-arrays) 및 [Julia Base section](@ref lib-arrays)를 참조하십시오.

`AbstractArray` 서브타입을 정의하는 데 중요한 부분은 [`IndexStyle`](@ref)입니다. 인덱싱은 배열의 중요한 부분이며 종종 핫 루프에서 발생하기 때문에, 인덱싱과 인덱스 할당을 가능한 한 효율적으로 만드는 것이 중요합니다. 배열 데이터 구조는 일반적으로 두 가지 방법 중 하나로 정의됩니다: 하나의 인덱스를 사용하여 요소에 가장 효율적으로 접근하거나(선형 인덱싱) 모든 차원에 대해 지정된 인덱스를 사용하여 본질적으로 요소에 접근합니다. 이 두 가지 방식은 Julia에서 `IndexLinear()`와 `IndexCartesian()`으로 식별됩니다. 선형 인덱스를 여러 인덱싱 서브스크립트로 변환하는 것은 일반적으로 매우 비쌉니다. 따라서 이는 모든 배열 유형에 대해 효율적인 일반 코드를 가능하게 하는 특성 기반 메커니즘을 제공합니다.

이 구분은 타입이 정의해야 하는 스칼라 인덱싱 방법을 결정합니다. `IndexLinear()` 배열은 간단합니다: `getindex(A::ArrayType, i::Int)`만 정의하면 됩니다. 배열이 이후 다차원 인덱스 집합으로 인덱싱될 때, 기본 제공되는 `getindex(A::AbstractArray, I...)`는 인덱스를 하나의 선형 인덱스로 효율적으로 변환한 다음 위의 메서드를 호출합니다. 반면 `IndexCartesian()` 배열은 `ndims(A)` `Int` 인덱스에 대해 지원되는 각 차원에 대해 메서드를 정의해야 합니다. 예를 들어, `SparseArrays` 표준 라이브러리 모듈의 [`SparseMatrixCSC`](@ref)는 두 차원만 지원하므로 `getindex(A::SparseMatrixCSC, i::Int, j::Int)`만 정의합니다. [`setindex!`](@ref)도 마찬가지입니다.

위의 제곱수 시퀀스로 돌아가면, 대신 `AbstractArray{Int, 1}`의 하위 유형으로 정의할 수 있습니다:

```jldoctest squarevectype
julia> struct SquaresVector <: AbstractArray{Int, 1}
           count::Int
       end

julia> Base.size(S::SquaresVector) = (S.count,)

julia> Base.IndexStyle(::Type{<:SquaresVector}) = IndexLinear()

julia> Base.getindex(S::SquaresVector, i::Int) = i*i
```

`AbstractArray`의 두 매개변수를 지정하는 것이 매우 중요하다는 점에 유의하십시오. 첫 번째 매개변수는 [`eltype`](@ref)를 정의하고, 두 번째 매개변수는 [`ndims`](@ref)를 정의합니다. 그 슈퍼타입과 이 세 가지 메서드만 있으면 `SquaresVector`는 반복 가능하고, 인덱스 가능하며, 완전히 기능적인 배열이 됩니다:

```jldoctest squarevectype
julia> s = SquaresVector(4)
4-element SquaresVector:
  1
  4
  9
 16

julia> s[s .> 8]
2-element Vector{Int64}:
  9
 16

julia> s + s
4-element Vector{Int64}:
  2
  8
 18
 32

julia> sin.(s)
4-element Vector{Float64}:
  0.8414709848078965
 -0.7568024953079282
  0.4121184852417566
 -0.2879033166650653
```

더 복잡한 예로, [`Dict`](@ref) 위에 구축된 자체 장난감 N차원 희소 배열 유형을 정의해 보겠습니다:

```jldoctest squarevectype
julia> struct SparseArray{T,N} <: AbstractArray{T,N}
           data::Dict{NTuple{N,Int}, T}
           dims::NTuple{N,Int}
       end

julia> SparseArray(::Type{T}, dims::Int...) where {T} = SparseArray(T, dims);

julia> SparseArray(::Type{T}, dims::NTuple{N,Int}) where {T,N} = SparseArray{T,N}(Dict{NTuple{N,Int}, T}(), dims);

julia> Base.size(A::SparseArray) = A.dims

julia> Base.similar(A::SparseArray, ::Type{T}, dims::Dims) where {T} = SparseArray(T, dims)

julia> Base.getindex(A::SparseArray{T,N}, I::Vararg{Int,N}) where {T,N} = get(A.data, I, zero(T))

julia> Base.setindex!(A::SparseArray{T,N}, v, I::Vararg{Int,N}) where {T,N} = (A.data[I] = v)
```

이것이 `IndexCartesian` 배열임을 주목하십시오. 따라서 우리는 배열의 차원에서 [`getindex`](@ref) 및 [`setindex!`](@ref)를 수동으로 정의해야 합니다. `SquaresVector`와는 달리, 우리는 `4d61726b646f776e2e436f64652822222c2022736574696e646578212229_40726566`를 정의할 수 있으므로 배열을 변형할 수 있습니다:

```jldoctest squarevectype
julia> A = SparseArray(Float64, 3, 3)
3×3 SparseArray{Float64, 2}:
 0.0  0.0  0.0
 0.0  0.0  0.0
 0.0  0.0  0.0

julia> fill!(A, 2)
3×3 SparseArray{Float64, 2}:
 2.0  2.0  2.0
 2.0  2.0  2.0
 2.0  2.0  2.0

julia> A[:] = 1:length(A); A
3×3 SparseArray{Float64, 2}:
 1.0  4.0  7.0
 2.0  5.0  8.0
 3.0  6.0  9.0
```

The result of indexing an `AbstractArray` can itself be an array (for instance when indexing by an `AbstractRange`). The `AbstractArray` fallback methods use [`similar`](@ref) to allocate an `Array` of the appropriate size and element type, which is filled in using the basic indexing method described above. However, when implementing an array wrapper you often want the result to be wrapped as well:

```jldoctest squarevectype
julia> A[1:2,:]
2×3 SparseArray{Float64, 2}:
 1.0  4.0  7.0
 2.0  5.0  8.0
```

이 예제에서는 `Base.similar(A::SparseArray, ::Type{T}, dims::Dims) where T`를 정의하여 적절한 래핑 배열을 생성함으로써 달성됩니다. (`similar`이 1개 및 2개 인수 형태를 지원하지만, 대부분의 경우 3개 인수 형태만 특수화하면 됩니다.) 이를 위해서는 `SparseArray`가 가변적이어야 하며(`setindex!`를 지원해야 함) `SparseArray`에 대해 `similar`, `getindex` 및 `setindex!`를 정의하면 배열을 [`copy`](@ref)할 수 있습니다.

```jldoctest squarevectype
julia> copy(A)
3×3 SparseArray{Float64, 2}:
 1.0  4.0  7.0
 2.0  5.0  8.0
 3.0  6.0  9.0
```

위의 모든 반복 가능하고 인덱스 가능한 메서드 외에도, 이러한 유형들은 서로 상호작용할 수 있으며 `AbstractArrays`에 대해 Julia Base에서 정의된 대부분의 메서드를 사용할 수 있습니다:

```jldoctest squarevectype
julia> A[SquaresVector(3)]
3-element SparseArray{Float64, 1}:
 1.0
 4.0
 9.0

julia> sum(A)
45.0
```

비전통적인 인덱싱(1이 아닌 다른 숫자에서 시작하는 인덱스)을 허용하는 배열 유형을 정의하는 경우, [`axes`](@ref)를 특수화해야 합니다. 또한 [`similar`](@ref)를 특수화하여 `dims` 인수(일반적으로 `Dims` 크기 튜플)가 `AbstractUnitRange` 객체를 수용할 수 있도록 해야 합니다. 아마도 당신이 설계한 범위 유형 `Ind`일 수 있습니다. 더 많은 정보는 [Arrays with custom indices](@ref man-custom-indices)를 참조하세요.

## [Strided Arrays](@id man-interface-strided-arrays)

| Methods to implement                     |                        | Brief description                                                                                                                                                                   |
|:---------------------------------------- |:---------------------- |:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `strides(A)`                             |                        | Return the distance in memory (in number of elements) between adjacent elements in each dimension as a tuple. If `A` is an `AbstractArray{T,0}`, this should return an empty tuple. |
| `Base.unsafe_convert(::Type{Ptr{T}}, A)` |                        | Return the native address of an array.                                                                                                                                              |
| `Base.elsize(::Type{<:A})`               |                        | Return the stride between consecutive elements in the array.                                                                                                                        |
| **Optional methods**                     | **Default definition** | **Brief description**                                                                                                                                                               |
| `stride(A, i::Int)`                      | `strides(A)[i]`        | Return the distance in memory (in number of elements) between adjacent elements in dimension k.                                                                                     |

스트라이드 배열은 메모리에 고정된 스트라이드로 저장된 항목을 가진 `AbstractArray`의 하위 유형입니다. 배열의 요소 유형이 BLAS와 호환되는 경우, 스트라이드 배열은 보다 효율적인 선형 대수 루틴을 위해 BLAS 및 LAPACK 루틴을 활용할 수 있습니다. 사용자 정의 스트라이드 배열의 전형적인 예는 추가 구조로 표준 `Array`를 래핑한 것입니다.

경고: 기본 저장소가 실제로 스트라이드가 아닌 경우 이러한 메서드를 구현하지 마십시오. 잘못된 결과나 세그멘테이션 오류가 발생할 수 있습니다.

여기 어떤 배열이 스트라이드 배열이고 어떤 배열이 아닌지를 보여주는 몇 가지 예가 있습니다:

```julia
1:5   # not strided (there is no storage associated with this array.)
Vector(1:5)  # is strided with strides (1,)
A = [1 5; 2 6; 3 7; 4 8]  # is strided with strides (1,4)
V = view(A, 1:2, :)   # is strided with strides (1,4)
V = view(A, 1:2:3, 1:2)   # is strided with strides (2,4)
V = view(A, [1,2,4], :)   # is not strided, as the spacing between rows is not fixed.
```

## [Customizing broadcasting](@id man-interfaces-broadcasting)

| Methods to implement                                       | Brief description                                                  |
|:---------------------------------------------------------- |:------------------------------------------------------------------ |
| `Base.BroadcastStyle(::Type{SrcType}) = SrcStyle()`        | Broadcasting behavior of `SrcType`                                 |
| `Base.similar(bc::Broadcasted{DestStyle}, ::Type{ElType})` | Allocation of output container                                     |
| **Optional methods**                                       |                                                                    |
| `Base.BroadcastStyle(::Style1, ::Style2) = Style12()`      | Precedence rules for mixing styles                                 |
| `Base.axes(x)`                                             | Declaration of the indices of `x`, as per [`axes(x)`](@ref).       |
| `Base.broadcastable(x)`                                    | Convert `x` to an object that has `axes` and supports indexing     |
| **Bypassing default machinery**                            |                                                                    |
| `Base.copy(bc::Broadcasted{DestStyle})`                    | Custom implementation of `broadcast`                               |
| `Base.copyto!(dest, bc::Broadcasted{DestStyle})`           | Custom implementation of `broadcast!`, specializing on `DestStyle` |
| `Base.copyto!(dest::DestType, bc::Broadcasted{Nothing})`   | Custom implementation of `broadcast!`, specializing on `DestType`  |
| `Base.Broadcast.broadcasted(f, args...)`                   | Override the default lazy behavior within a fused expression       |
| `Base.Broadcast.instantiate(bc::Broadcasted{DestStyle})`   | Override the computation of the lazy broadcast's axes              |

[Broadcasting](@ref)는 `broadcast` 또는 `broadcast!`에 대한 명시적 호출에 의해 트리거되거나, `A .+ b` 또는 `f.(x, y)`와 같은 "점" 연산에 의해 암묵적으로 트리거됩니다. [`axes`](@ref)를 가지고 있고 인덱싱을 지원하는 모든 객체는 브로드캐스팅의 인수로 참여할 수 있으며, 기본적으로 결과는 `Array`에 저장됩니다. 이 기본 프레임워크는 세 가지 주요 방법으로 확장 가능합니다:

  * 모든 인수가 브로드캐스트를 지원하도록 보장하기
  * 주어진 인수 집합에 적합한 출력 배열 선택하기
  * 주어진 인수 집합에 대한 효율적인 구현 선택

모든 유형이 `axes` 및 인덱싱을 지원하는 것은 아니지만, 많은 유형이 브로드캐스트에서 허용되는 것이 편리합니다. [`Base.broadcastable`](@ref) 함수는 브로드캐스트할 각 인수에 대해 호출되어, `axes` 및 인덱싱을 지원하는 다른 것을 반환할 수 있습니다. 기본적으로, 이는 모든 `AbstractArray`와 `Number`에 대한 항등 함수입니다. — 이들은 이미 `axes` 및 인덱싱을 지원합니다.

만약 어떤 타입이 "0차원 스칼라" (단일 객체)처럼 작동하도록 의도되었다면, 다음과 같은 메서드를 정의해야 합니다:

```julia
Base.broadcastable(o::MyType) = Ref(o)
```

인수는 0차원 [`Ref`](@ref) 컨테이너에 래핑되어 반환됩니다. 예를 들어, 이러한 래퍼 메서드는 타입 자체, 함수, [`missing`](@ref) 및 [`nothing`](@ref)와 같은 특별한 싱글톤 및 날짜에 대해 정의됩니다.

사용자 정의 배열 유사 타입은 `Base.broadcastable`을 전문화하여 자신의 형태를 정의할 수 있지만, `collect(Base.broadcastable(x)) == collect(x)`라는 규칙을 따라야 합니다. 주목할 만한 예외는 `AbstractString`입니다. 문자열은 문자들의 반복 가능한 컬렉션임에도 불구하고 브로드캐스트의 목적을 위해 스칼라처럼 동작하도록 특별히 처리됩니다(자세한 내용은 [Strings](@ref)을 참조하십시오).

다음 두 단계(출력 배열 선택 및 구현)는 주어진 인수 집합에 대한 단일 답변을 결정하는 데 의존합니다. 브로드캐스트는 모든 다양한 유형의 인수를 수집하여 단 하나의 출력 배열과 하나의 구현으로 축소해야 합니다. 브로드캐스트는 이 단일 답변을 "스타일"이라고 부릅니다. 각 브로드캐스트 가능한 객체는 고유한 선호 스타일을 가지고 있으며, 이러한 스타일을 단일 답변인 "목적지 스타일"로 결합하기 위해 프로모션과 유사한 시스템이 사용됩니다.

### Broadcast Styles

`Base.BroadcastStyle`는 모든 브로드캐스트 스타일이 파생되는 추상 유형입니다. 함수로 사용될 때 두 가지 가능한 형태가 있으며, 단항(단일 인수) 및 이항입니다. 단항 변형은 특정 브로드캐스트 동작 및/또는 출력 유형을 구현할 의도가 있음을 나타내며, 기본 폴백 [`Broadcast.DefaultArrayStyle`](@ref)에 의존하고 싶지 않음을 나타냅니다.

이 기본값을 재정의하려면, 객체에 대한 사용자 정의 `BroadcastStyle`을 정의할 수 있습니다:

```julia
struct MyStyle <: Broadcast.BroadcastStyle end
Base.BroadcastStyle(::Type{<:MyType}) = MyStyle()
```

경우에 따라 `MyStyle`을 정의하지 않는 것이 편리할 수 있으며, 이 경우 일반 방송 래퍼 중 하나를 활용할 수 있습니다:

  * `Base.BroadcastStyle(::Type{<:MyType}) = Broadcast.Style{MyType}()`는 임의의 타입에 사용할 수 있습니다.
  * `Base.BroadcastStyle(::Type{<:MyType}) = Broadcast.ArrayStyle{MyType}()`는 `MyType`이 `AbstractArray`인 경우 선호됩니다.
  * `N` 차원만 지원하는 `AbstractArrays`의 경우, `Broadcast.AbstractArrayStyle{N}`의 하위 유형을 생성합니다.

방송 작업이 여러 인수를 포함할 때, 개별 인수 스타일이 결합되어 출력 컨테이너의 유형을 제어하는 단일 `DestStyle`이 결정됩니다. 자세한 내용은 [below](@ref writing-binary-broadcasting-rules)를 참조하세요.

### Selecting an appropriate output array

브로드캐스트 스타일은 디스패치 및 특수화를 허용하기 위해 모든 브로드캐스팅 작업에 대해 계산됩니다. 결과 배열의 실제 할당은 `similar`에 의해 처리되며, 브로드캐스트된 객체가 첫 번째 인수로 사용됩니다.

```julia
Base.similar(bc::Broadcasted{DestStyle}, ::Type{ElType})
```

대체 정의는

```julia
similar(bc::Broadcasted{DefaultArrayStyle{N}}, ::Type{ElType}) where {N,ElType} =
    similar(Array{ElType}, axes(bc))
```

그러나 필요하다면 이러한 인수 중 하나 또는 모두에 대해 전문화할 수 있습니다. 마지막 인수 `bc`는 (잠재적으로 융합된) 브로드캐스트 작업의 게으른 표현인 `Broadcasted` 객체입니다. 이러한 목적을 위해 래퍼의 가장 중요한 필드는 함수와 인수 목록을 설명하는 `f`와 `args`입니다. 인수 목록에는 다른 중첩된 `Broadcasted` 래퍼가 포함될 수 있으며, 실제로 자주 포함됩니다.

완전한 예를 들자면, `ArrayAndChar`라는 타입을 생성하여 배열과 단일 문자를 저장했다고 가정해 보겠습니다:

```jldoctest ArrayAndChar; output = false
struct ArrayAndChar{T,N} <: AbstractArray{T,N}
    data::Array{T,N}
    char::Char
end
Base.size(A::ArrayAndChar) = size(A.data)
Base.getindex(A::ArrayAndChar{T,N}, inds::Vararg{Int,N}) where {T,N} = A.data[inds...]
Base.setindex!(A::ArrayAndChar{T,N}, val, inds::Vararg{Int,N}) where {T,N} = A.data[inds...] = val
Base.showarg(io::IO, A::ArrayAndChar, toplevel) = print(io, typeof(A), " with char '", A.char, "'")
# output

```

브로드캐스팅이 `char` "메타데이터"를 보존하도록 하려면, 먼저 정의합니다.

```jldoctest ArrayAndChar; output = false
Base.BroadcastStyle(::Type{<:ArrayAndChar}) = Broadcast.ArrayStyle{ArrayAndChar}()
# output

```

이는 우리가 해당 `similar` 메서드도 정의해야 함을 의미합니다:

```jldoctest ArrayAndChar; output = false
function Base.similar(bc::Broadcast.Broadcasted{Broadcast.ArrayStyle{ArrayAndChar}}, ::Type{ElType}) where ElType
    # Scan the inputs for the ArrayAndChar:
    A = find_aac(bc)
    # Use the char field of A to create the output
    ArrayAndChar(similar(Array{ElType}, axes(bc)), A.char)
end

"`A = find_aac(As)` returns the first ArrayAndChar among the arguments."
find_aac(bc::Base.Broadcast.Broadcasted) = find_aac(bc.args)
find_aac(args::Tuple) = find_aac(find_aac(args[1]), Base.tail(args))
find_aac(x) = x
find_aac(::Tuple{}) = nothing
find_aac(a::ArrayAndChar, rest) = a
find_aac(::Any, rest) = find_aac(rest)
# output
find_aac (generic function with 6 methods)
```

이 정의들로부터 다음과 같은 행동을 얻을 수 있다:

```jldoctest ArrayAndChar
julia> a = ArrayAndChar([1 2; 3 4], 'x')
2×2 ArrayAndChar{Int64, 2} with char 'x':
 1  2
 3  4

julia> a .+ 1
2×2 ArrayAndChar{Int64, 2} with char 'x':
 2  3
 4  5

julia> a .+ [5,10]
2×2 ArrayAndChar{Int64, 2} with char 'x':
  6   7
 13  14
```

### [Extending broadcast with custom implementations](@id extending-in-place-broadcast)

일반적으로, 브로드캐스트 작업은 적용할 함수와 그 인수를 함께 보유하는 게으른 `Broadcasted` 컨테이너로 표현됩니다. 이러한 인수는 더 중첩된 `Broadcasted` 컨테이너일 수 있으며, 평가될 큰 표현식 트리를 형성합니다. 중첩된 `Broadcasted` 컨테이너의 트리는 암시적 점 구문을 통해 직접 구성됩니다; 예를 들어, `5 .+ 2.*x`는 일시적으로 `Broadcasted(+, 5, Broadcasted(*, 2, x))`로 표현됩니다. 이는 사용자가 즉시 `copy` 호출을 통해 실현되기 때문에 보이지 않지만, 이 컨테이너가 사용자 정의 유형의 저자에게 브로드캐스트의 확장성을 제공하는 기초를 제공합니다. 내장된 브로드캐스트 기계는 그런 다음 인수에 따라 결과 유형과 크기를 결정하고, 이를 할당한 다음, 기본 `copyto!(::AbstractArray, ::Broadcasted)` 메서드를 사용하여 `Broadcasted` 객체의 실현을 복사합니다. 내장된 폴백 `broadcast` 및 `broadcast!` 메서드도 유사하게 작업의 일시적인 `Broadcasted` 표현을 구성하여 동일한 코드 경로를 따를 수 있도록 합니다. 이를 통해 사용자 정의 배열 구현이 브로드캐스팅을 사용자화하고 최적화하기 위해 자체 `copyto!` 특수화를 제공할 수 있습니다. 이는 계산된 브로드캐스트 스타일에 의해 다시 결정됩니다. 이는 작업의 매우 중요한 부분으로, `Broadcasted` 유형의 첫 번째 유형 매개변수로 저장되어 디스패치 및 특수화를 가능하게 합니다.

일부 유형의 경우, 중첩된 브로드캐스팅 수준에서 연산을 "융합"하는 기계가 없거나 점진적으로 더 효율적으로 수행될 수 있습니다. 이러한 경우, `x .* (x .+ 1)`을 `broadcast(*, x, broadcast(+, x, 1))`로 작성된 것처럼 평가해야 할 수도 있습니다. 여기서 내부 연산은 외부 연산을 처리하기 전에 평가됩니다. 이러한 종류의 즉각적인 연산은 약간의 간접 지원을 통해 직접 지원됩니다. Julia는 융합된 표현식 `x .* (x .+ 1)`을 `Broadcast.broadcasted(*, x, Broadcast.broadcasted(+, x, 1))`로 낮춥니다. 이제 기본적으로 `broadcasted`는 융합된 표현식 트리의 지연 표현을 생성하기 위해 `Broadcasted` 생성자를 호출하지만, 특정 함수와 인수 조합에 대해 이를 재정의하도록 선택할 수 있습니다.

예를 들어, 내장된 `AbstractRange` 객체는 시작, 단계 및 길이(또는 정지)를 기준으로 순수하게 즉시 평가할 수 있는 브로드캐스트된 표현의 조각을 최적화하기 위해 이 기계를 사용합니다. 다른 모든 기계와 마찬가지로 `broadcasted`는 인수의 결합된 브로드캐스트 스타일을 계산하고 노출하므로, `broadcasted(f, args...)`에 특화하는 대신 `broadcasted(::DestStyle, f, args...)`에 대해 스타일, 함수 및 인수의 조합에 따라 특화할 수 있습니다.

예를 들어, 다음 정의는 범위의 부정을 지원합니다:

```julia
broadcasted(::DefaultArrayStyle{1}, ::typeof(-), r::OrdinalRange) = range(-first(r), step=-step(r), length=length(r))
```

### [Extending in-place broadcasting](@id extending-in-place-broadcast)

인플레이스 브로드캐스팅은 적절한 `copyto!(dest, bc::Broadcasted)` 메서드를 정의함으로써 지원될 수 있습니다. `dest` 또는 `bc`의 특정 하위 유형에 대해 특수화하고 싶을 수 있으므로 패키지 간의 모호성을 피하기 위해 다음과 같은 규칙을 권장합니다.

특정 스타일 `DestStyle`에 특화하고 싶다면, 메서드를 정의하세요.

```julia
copyto!(dest, bc::Broadcasted{DestStyle})
```

선택적으로, 이 양식을 사용하여 `dest`의 유형에 대해서도 전문화할 수 있습니다.

대신 `DestStyle`에 대한 특수화 없이 목적지 유형 `DestType`에 특화하고 싶다면, 다음 서명을 가진 메서드를 정의해야 합니다:

```julia
copyto!(dest::DestType, bc::Broadcasted{Nothing})
```

이것은 래퍼를 `Broadcasted{Nothing}`으로 변환하는 `copyto!`의 대체 구현을 활용합니다. 결과적으로 `DestType`에 대한 전문화는 `DestStyle`에 대한 전문화보다 우선 순위가 낮습니다.

유사하게, `copy(::Broadcasted)` 메서드를 사용하여 부적절한 브로드캐스팅을 완전히 무시할 수 있습니다.

#### Working with `Broadcasted` objects

이러한 `copy` 또는 `copyto!` 메서드를 구현하기 위해서는 물론 각 요소를 계산하기 위해 `Broadcasted` 래퍼와 함께 작업해야 합니다. 이를 수행하는 두 가지 주요 방법이 있습니다:

  * `Broadcast.flatten`는 잠재적으로 중첩된 연산을 단일 함수와 평면 인수 목록으로 다시 계산합니다. 방송 모양 규칙을 직접 구현해야 하지만, 이는 제한된 상황에서 유용할 수 있습니다.
  * `axes(::Broadcasted)`의 `CartesianIndices`를 반복하고 결과 `CartesianIndex` 객체로 인덱싱하여 결과를 계산합니다.

### [Writing binary broadcasting rules](@id writing-binary-broadcasting-rules)

우선순위 규칙은 이진 `BroadcastStyle` 호출에 의해 정의됩니다:

```julia
Base.BroadcastStyle(::Style1, ::Style2) = Style12()
```

`Style12`는 `Style1` 및 `Style2`의 인수를 포함하는 출력에 대해 선택하고자 하는 `BroadcastStyle`입니다. 예를 들어,

```julia
Base.BroadcastStyle(::Broadcast.Style{Tuple}, ::Broadcast.AbstractArrayStyle{0}) = Broadcast.Style{Tuple}()
```

`Tuple`가 0차원 배열보다 "우선"한다는 것을 나타냅니다(출력 컨테이너는 튜플이 됩니다). 사용자가 인수를 어떤 순서로 제공하든 관계없이 하나의 인수 순서만 정의하면 충분하다는 점에 유의해야 합니다.

`AbstractArray` 유형의 경우, `BroadcastStyle`을 정의하면 기본 선택인 [`Broadcast.DefaultArrayStyle`](@ref)를 대체합니다. `DefaultArrayStyle`과 추상 슈퍼타입인 `AbstractArrayStyle`은 고정된 차원 요구 사항이 있는 특수 배열 유형을 지원하기 위해 차원 수를 유형 매개변수로 저장합니다.

`DefaultArrayStyle`는 다음 메서드들 때문에 정의된 다른 모든 `AbstractArrayStyle`에 "패배"합니다:

```julia
BroadcastStyle(a::AbstractArrayStyle{Any}, ::DefaultArrayStyle) = a
BroadcastStyle(a::AbstractArrayStyle{N}, ::DefaultArrayStyle{N}) where N = a
BroadcastStyle(a::AbstractArrayStyle{M}, ::DefaultArrayStyle{N}) where {M,N} =
    typeof(a)(Val(max(M, N)))
```

이진 `BroadcastStyle` 규칙을 작성할 필요는 없지만, 두 개 이상의 비-`DefaultArrayStyle` 유형에 대한 우선 순위를 설정하려는 경우에는 작성할 수 있습니다.

배열 유형이 고정 차원 요구 사항이 있는 경우 `AbstractArrayStyle`을 서브타입으로 만들어야 합니다. 예를 들어, 희소 배열 코드는 다음과 같은 정의를 가지고 있습니다:

```julia
struct SparseVecStyle <: Broadcast.AbstractArrayStyle{1} end
struct SparseMatStyle <: Broadcast.AbstractArrayStyle{2} end
Base.BroadcastStyle(::Type{<:SparseVector}) = SparseVecStyle()
Base.BroadcastStyle(::Type{<:SparseMatrixCSC}) = SparseMatStyle()
```

`AbstractArrayStyle`를 서브타입화할 때마다, `Val(N)` 인수를 받는 스타일의 생성자를 만들어 차원 결합 규칙을 정의해야 합니다. 예를 들어:

```julia
SparseVecStyle(::Val{0}) = SparseVecStyle()
SparseVecStyle(::Val{1}) = SparseVecStyle()
SparseVecStyle(::Val{2}) = SparseMatStyle()
SparseVecStyle(::Val{N}) where N = Broadcast.DefaultArrayStyle{N}()
```

이 규칙은 `SparseVecStyle`과 0차 또는 1차 배열의 조합이 또 다른 `SparseVecStyle`을 생성하고, 2차원 배열과의 조합이 `SparseMatStyle`을 생성하며, 더 높은 차원의 경우 밀집 임의 차원 프레임워크로 돌아간다는 것을 나타냅니다. 이러한 규칙은 브로드캐스팅이 1차원 또는 2차원 출력을 생성하는 연산에 대해 희소 표현을 유지하도록 허용하지만, 다른 차원에 대해서는 `Array`를 생성합니다.

## [Instance Properties](@id man-instance-properties)

| Methods to implement                             | Default definition      | Brief description                                                                                                                              |
|:------------------------------------------------ |:----------------------- |:---------------------------------------------------------------------------------------------------------------------------------------------- |
| `propertynames(x::ObjType, private::Bool=false)` | `fieldnames(typeof(x))` | Return a tuple of the properties (`x.property`) of an object `x`. If `private=true`, also return property names intended to be kept as private |
| `getproperty(x::ObjType, s::Symbol)`             | `getfield(x, s)`        | Return property `s` of `x`. `x.s` calls `getproperty(x, :s)`.                                                                                  |
| `setproperty!(x::ObjType, s::Symbol, v)`         | `setfield!(x, s, v)`    | Set property `s` of `x` to `v`. `x.s = v` calls `setproperty!(x, :s, v)`. Should return `v`.                                                   |

때때로 최종 사용자가 객체의 필드와 상호작용하는 방식을 변경하는 것이 바람직할 수 있습니다. 타입 필드에 대한 직접적인 접근을 허용하는 대신, 사용자와 코드 사이에 추가적인 추상화 계층을 제공하기 위해 `object.field`를 오버로딩할 수 있습니다. 속성은 사용자가 객체에서 *보는 것*이고, 필드는 객체가 *실제로 무엇인지*입니다.

기본적으로 속성과 필드는 동일합니다. 그러나 이 동작은 변경할 수 있습니다. 예를 들어, [polar coordinates](https://en.wikipedia.org/wiki/Polar_coordinate_system)에서 평면의 점을 나타내는 이 표현을 살펴보세요:

```jldoctest polartype
julia> mutable struct Point
           r::Float64
           ϕ::Float64
       end

julia> p = Point(7.0, pi/4)
Point(7.0, 0.7853981633974483)
```

위의 표에 설명된 대로 점 접근 `p.r`은 기본적으로 `getproperty(p, :r)`와 같으며, 이는 기본적으로 `getfield(p, :r)`와 같습니다:

```jldoctest polartype
julia> propertynames(p)
(:r, :ϕ)

julia> getproperty(p, :r), getproperty(p, :ϕ)
(7.0, 0.7853981633974483)

julia> p.r, p.ϕ
(7.0, 0.7853981633974483)

julia> getfield(p, :r), getproperty(p, :ϕ)
(7.0, 0.7853981633974483)
```

그러나 우리는 사용자가 `Point`가 좌표를 `r`과 `ϕ`(필드)로 저장한다는 사실을 모르게 하고 대신 `x`와 `y`(속성)와 상호작용하기를 원할 수 있습니다. 첫 번째 열의 메서드는 새로운 기능을 추가하도록 정의될 수 있습니다:

```jldoctest polartype
julia> Base.propertynames(::Point, private::Bool=false) = private ? (:x, :y, :r, :ϕ) : (:x, :y)

julia> function Base.getproperty(p::Point, s::Symbol)
           if s === :x
               return getfield(p, :r) * cos(getfield(p, :ϕ))
           elseif s === :y
               return getfield(p, :r) * sin(getfield(p, :ϕ))
           else
               # This allows accessing fields with p.r and p.ϕ
               return getfield(p, s)
           end
       end

julia> function Base.setproperty!(p::Point, s::Symbol, f)
           if s === :x
               y = p.y
               setfield!(p, :r, sqrt(f^2 + y^2))
               setfield!(p, :ϕ, atan(y, f))
               return f
           elseif s === :y
               x = p.x
               setfield!(p, :r, sqrt(x^2 + f^2))
               setfield!(p, :ϕ, atan(f, x))
               return f
           else
               # This allow modifying fields with p.r and p.ϕ
               return setfield!(p, s, f)
           end
       end
```

`getproperty`와 `setproperty!` 내부에서 `getfield`와 `setfield`를 사용하는 것이 중요합니다. 점(.) 구문을 사용하면 함수가 재귀적으로 호출되어 타입 추론 문제를 일으킬 수 있습니다. 이제 새로운 기능을 시도해 볼 수 있습니다:

```jldoctest polartype
julia> propertynames(p)
(:x, :y)

julia> p.x
4.949747468305833

julia> p.y = 4.0
4.0

julia> p.r
6.363961030678928
```

마지막으로, 이렇게 인스턴스 속성을 추가하는 것은 줄리아에서 매우 드물게 이루어지며, 일반적으로 그렇게 하는 데에는 충분한 이유가 있어야 한다는 점을 언급할 가치가 있다.

## [Rounding](@id man-rounding-interface)

| Methods to implement                          | Default definition        | Brief description                                                                                   |
|:--------------------------------------------- |:------------------------- |:--------------------------------------------------------------------------------------------------- |
| `round(x::ObjType, r::RoundingMode)`          | none                      | Round `x` and return the result. If possible, round should return an object of the same type as `x` |
| `round(T::Type, x::ObjType, r::RoundingMode)` | `convert(T, round(x, r))` | Round `x`, returning the result as a `T`                                                            |

새로운 유형에서 반올림을 지원하려면 일반적으로 단일 메서드 `round(x::ObjType, r::RoundingMode)`를 정의하는 것으로 충분합니다. 전달된 반올림 모드는 값이 어떤 방향으로 반올림되어야 하는지를 결정합니다. 가장 일반적으로 사용되는 반올림 모드는 `RoundNearest`, `RoundToZero`, `RoundDown`, 및 `RoundUp`이며, 이러한 반올림 모드는 각각 하나의 인수를 가지는 `round`, 메서드, 및 `trunc`, `floor`, `ceil`의 정의에서 사용됩니다.

일부 경우, 두 개의 인수 메서드 뒤에 변환을 따르는 것보다 더 정확하거나 성능이 좋은 세 개의 인수 `round` 메서드를 정의하는 것이 가능합니다. 이 경우 두 개의 인수 메서드 외에 세 개의 인수 메서드를 정의하는 것이 허용됩니다. 반올림된 결과를 `T` 유형의 객체로 표현할 수 없는 경우, 세 개의 인수 메서드는 `InexactError`를 발생시켜야 합니다.

예를 들어, https://github.com/JuliaPhysics/Measurements.jl와 유사한 가능한 값의 범위를 나타내는 `Interval` 유형이 있는 경우, 다음과 같이 해당 유형에 대한 반올림을 정의할 수 있습니다.

```jldoctest
julia> struct Interval{T}
           min::T
           max::T
       end

julia> Base.round(x::Interval, r::RoundingMode) = Interval(round(x.min, r), round(x.max, r))

julia> x = Interval(1.7, 2.2)
Interval{Float64}(1.7, 2.2)

julia> round(x)
Interval{Float64}(2.0, 2.0)

julia> floor(x)
Interval{Float64}(1.0, 2.0)

julia> ceil(x)
Interval{Float64}(2.0, 3.0)

julia> trunc(x)
Interval{Float64}(1.0, 2.0)
```
