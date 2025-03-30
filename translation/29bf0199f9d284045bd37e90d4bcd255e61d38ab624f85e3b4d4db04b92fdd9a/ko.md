```
findmax(A; dims) -> (maxval, index)
```

배열 입력에 대해 주어진 차원에서 최대값과 인덱스를 반환합니다. `NaN`은 `missing`을 제외한 모든 다른 값보다 큰 것으로 간주됩니다.

# 예제

```jldoctest
julia> A = [1.0 2; 3 4]
2×2 Matrix{Float64}:
 1.0  2.0
 3.0  4.0

julia> findmax(A, dims=1)
([3.0 4.0], CartesianIndex{2}[CartesianIndex(2, 1) CartesianIndex(2, 2)])

julia> findmax(A, dims=2)
([2.0; 4.0;;], CartesianIndex{2}[CartesianIndex(1, 2); CartesianIndex(2, 2);;])
```
