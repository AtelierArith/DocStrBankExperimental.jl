```
sortperm!(ix, A; alg::Algorithm=DEFAULT_UNSTABLE, lt=isless, by=identity, rev::Bool=false, order::Ordering=Forward, [dims::Integer])
```

[`sortperm`](@ref)와 유사하지만, `A`와 동일한 `axes`를 가진 미리 할당된 인덱스 벡터 또는 배열 `ix`를 허용합니다. `ix`는 `LinearIndices(A)`의 값을 포함하도록 초기화됩니다.

!!! 경고     변형된 인수가 다른 인수와 메모리를 공유할 경우 동작이 예기치 않게 될 수 있습니다.

!!! 호환성 "Julia 1.9"     `dims`를 허용하는 메서드는 최소한 Julia 1.9가 필요합니다.

# 예제

```jldoctest
julia> v = [3, 1, 2]; p = zeros(Int, 3);

julia> sortperm!(p, v); p
3-element Vector{Int64}:
 2
 3
 1

julia> v[p]
3-element Vector{Int64}:
 1
 2
 3

julia> A = [8 7; 5 6]; p = zeros(Int,2, 2);

julia> sortperm!(p, A; dims=1); p
2×2 Matrix{Int64}:
 2  4
 1  3

julia> sortperm!(p, A; dims=2); p
2×2 Matrix{Int64}:
 3  1
 2  4
```
