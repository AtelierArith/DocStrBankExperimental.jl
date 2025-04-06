```
eigvecs(A; permute::Bool=true, scale::Bool=true, `sortby`) -> Matrix
```

행렬 `A`의 고유벡터로 구성된 행렬 `M`을 반환합니다. (`k`번째 고유벡터는 슬라이스 `M[:, k]`에서 얻을 수 있습니다.) `permute`, `scale`, 및 `sortby` 키워드는 [`eigen`](@ref)와 동일합니다.

# 예제

```jldoctest
julia> eigvecs([1.0 0.0 0.0; 0.0 3.0 0.0; 0.0 0.0 18.0])
3×3 Matrix{Float64}:
 1.0  0.0  0.0
 0.0  1.0  0.0
 0.0  0.0  1.0
```
