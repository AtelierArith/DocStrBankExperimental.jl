```
sortperm(A; alg::Algorithm=DEFAULT_UNSTABLE, lt=isless, by=identity, rev::Bool=false, order::Ordering=Forward, [dims::Integer])
```

주어진 차원에서 `A[I]`를 정렬된 순서로 배치하는 순열 벡터 또는 배열 `I`를 반환합니다. `A`가 여러 차원을 가지는 경우, `dims` 키워드 인수를 지정해야 합니다. 순서는 [`sort!`](@ref)와 동일한 키워드를 사용하여 지정됩니다. 정렬 알고리즘이 불안정하더라도 순열은 안정적일 것이며, 동일한 요소의 인덱스는 오름차순으로 나타납니다.

또한 [`sortperm!`](@ref), [`partialsortperm`](@ref), [`invperm`](@ref), [`indexin`](@ref)도 참조하십시오. 배열의 슬라이스를 정렬하려면 [`sortslices`](@ref)를 참조하십시오.

!!! compat "Julia 1.9"
    `dims`를 수용하는 메서드는 최소한 Julia 1.9가 필요합니다.


# 예제

```jldoctest
julia> v = [3, 1, 2];

julia> p = sortperm(v)
3-element Vector{Int64}:
 2
 3
 1

julia> v[p]
3-element Vector{Int64}:
 1
 2
 3

julia> A = [8 7; 5 6]
2×2 Matrix{Int64}:
 8  7
 5  6

julia> sortperm(A, dims = 1)
2×2 Matrix{Int64}:
 2  4
 1  3

julia> sortperm(A, dims = 2)
2×2 Matrix{Int64}:
 3  1
 2  4
```
