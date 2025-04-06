```
eigvals(A; permute::Bool=true, scale::Bool=true, sortby) -> values
```

행렬 `A`의 고유값을 반환합니다.

일반 비대칭 행렬의 경우 고유값 계산 전에 행렬이 어떻게 균형을 이루는지 지정할 수 있습니다. `permute`, `scale`, 및 `sortby` 키워드는 [`eigen`](@ref)와 동일합니다.

# 예제

```jldoctest
julia> diag_matrix = [1 0; 0 4]
2×2 Matrix{Int64}:
 1  0
 0  4

julia> eigvals(diag_matrix)
2-element Vector{Float64}:
 1.0
 4.0
```
