# Sorting and Related Functions

줄리아는 이미 정렬된 값 배열을 정렬하고 상호작용하는 데 있어 광범위하고 유연한 API를 제공합니다. 기본적으로 줄리아는 합리적인 알고리즘을 선택하고 오름차순으로 정렬합니다:

```jldoctest
julia> sort([2,3,1])
3-element Vector{Int64}:
 1
 2
 3
```

역순으로 정렬할 수도 있습니다:

```jldoctest
julia> sort([2,3,1], rev=true)
3-element Vector{Int64}:
 3
 2
 1
```

`sort`는 입력을 변경하지 않고 정렬된 복사본을 생성합니다. 기존 배열을 변형하려면 "bang" 버전의 정렬 함수를 사용하세요:

```jldoctest
julia> a = [2,3,1];

julia> sort!(a);

julia> a
3-element Vector{Int64}:
 1
 2
 3
```

배열을 직접 정렬하는 대신, 배열을 정렬된 순서로 배치하는 배열의 인덱스의 순열을 계산할 수 있습니다:

```julia-repl
julia> v = randn(5)
5-element Array{Float64,1}:
  0.297288
  0.382396
 -0.597634
 -0.0104452
 -0.839027

julia> p = sortperm(v)
5-element Array{Int64,1}:
 5
 3
 4
 1
 2

julia> v[p]
5-element Array{Float64,1}:
 -0.839027
 -0.597634
 -0.0104452
  0.297288
  0.382396
```

배열은 값의 임의 변환에 따라 정렬될 수 있습니다:

```julia-repl
julia> sort(v, by=abs)
5-element Array{Float64,1}:
 -0.0104452
  0.297288
  0.382396
 -0.597634
 -0.839027
```

또는 변환에 의해 역순으로:

```julia-repl
julia> sort(v, by=abs, rev=true)
5-element Array{Float64,1}:
 -0.839027
 -0.597634
  0.382396
  0.297288
 -0.0104452
```

필요한 경우, 정렬 알고리즘을 선택할 수 있습니다:

```julia-repl
julia> sort(v, alg=InsertionSort)
5-element Array{Float64,1}:
 -0.839027
 -0.597634
 -0.0104452
  0.297288
  0.382396
```

모든 정렬 및 순서 관련 함수는 조작할 값에 대해 [strict weak order](https://en.wikipedia.org/wiki/Weak_ordering#Strict_weak_orderings)를 정의하는 "작다" 관계에 의존합니다. 기본적으로 `isless` 함수가 호출되지만, 관계는 `lt` 키워드를 통해 지정할 수 있으며, 이 함수는 두 배열 요소를 받아들이고 첫 번째 인수가 두 번째 인수보다 "작다"면 `true`를 반환합니다. 더 많은 정보는 [`sort!`](@ref) 및 [Alternate Orderings](@ref)를 참조하십시오.

## Sorting Functions

```@docs
Base.sort!
Base.sort
Base.sortperm
Base.InsertionSort
Base.MergeSort
Base.QuickSort
Base.PartialQuickSort
Base.Sort.sortperm!
Base.Sort.sortslices
```

## Order-Related Functions

```@docs
Base.issorted
Base.Sort.searchsorted
Base.Sort.searchsortedfirst
Base.Sort.searchsortedlast
Base.Sort.insorted
Base.Sort.partialsort!
Base.Sort.partialsort
Base.Sort.partialsortperm
Base.Sort.partialsortperm!
```

## Sorting Algorithms

현재 기본 Julia에서 공개적으로 사용할 수 있는 정렬 알고리즘은 네 가지입니다:

  * [`InsertionSort`](@ref)
  * [`QuickSort`](@ref)
  * [`PartialQuickSort(k)`](@ref)
  * [`MergeSort`](@ref)

기본적으로 `sort` 함수 패밀리는 대부분의 입력에 대해 빠른 안정 정렬 알고리즘을 사용합니다. 정확한 알고리즘 선택은 향후 성능 개선을 허용하기 위한 구현 세부 사항입니다. 현재는 입력 유형, 크기 및 구성에 따라 `RadixSort`, `ScratchQuickSort`, `InsertionSort` 및 `CountingSort`의 하이브리드가 사용됩니다. 구현 세부 사항은 변경될 수 있지만 현재 `??Base.DEFAULT_STABLE`의 확장 도움말과 그곳에 나열된 내부 정렬 알고리즘의 docstring에서 확인할 수 있습니다.

`alg` 키워드를 사용하여 선호하는 알고리즘을 명시적으로 지정할 수 있습니다 (예: `sort!(v, alg=PartialQuickSort(10:20))`) 또는 `Base.Sort.defalg` 함수에 특수화된 메서드를 추가하여 사용자 정의 유형에 대한 기본 정렬 알고리즘을 재구성할 수 있습니다. 예를 들어, [InlineStrings.jl](https://github.com/JuliaStrings/InlineStrings.jl/blob/v1.3.2/src/InlineStrings.jl#L903)는 다음 메서드를 정의합니다:

```julia
Base.Sort.defalg(::AbstractArray{<:Union{SmallInlineStrings, Missing}}) = InlineStringSort
```

!!! compat "Julia 1.9"
    기본 정렬 알고리즘(`Base.Sort.defalg`에서 반환됨)은 Julia 1.9부터 안정성이 보장됩니다. 이전 버전에서는 숫자 배열을 정렬할 때 불안정한 엣지 케이스가 있었습니다.


## Alternate Orderings

기본적으로, `sort`, `searchsorted` 및 관련 함수는 두 요소를 비교하여 어떤 것이 먼저 와야 하는지를 결정하기 위해 [`isless`](@ref)를 사용합니다. [`Base.Order.Ordering`](@ref) 추상 유형은 동일한 요소 집합에 대해 대체 정렬을 정의하는 메커니즘을 제공합니다: `sort!`와 같은 정렬 함수를 호출할 때, `order`라는 키워드 인수와 함께 `Ordering`의 인스턴스를 제공할 수 있습니다.

`Ordering`의 인스턴스는 [`Base.Order.lt`](@ref) 함수에 의해 순서를 정의하며, 이는 `isless`의 일반화로 작동합니다. 이 함수의 사용자 정의 `Ordering`에 대한 동작은 [strict weak order](https://en.wikipedia.org/wiki/Weak_ordering#Strict_weak_orderings)의 모든 조건을 충족해야 합니다. 유효하고 무효한 `lt` 함수에 대한 세부정보와 예시는 [`sort!`](@ref)를 참조하십시오.

```@docs
Base.Order.Ordering
Base.Order.lt
Base.Order.ord
Base.Order.Forward
Base.Order.ReverseOrdering
Base.Order.Reverse
Base.Order.By
Base.Order.Lt
Base.Order.Perm
```
