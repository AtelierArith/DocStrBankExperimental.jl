```
findmin(A; dims) -> (minval, index)
```

배열 입력에 대해 주어진 차원에서 최소값과 인덱스를 반환합니다. `NaN`은 `missing`을 제외한 모든 값보다 작게 처리됩니다.

# 예제

```jldoctest
julia> A = [1.0 2; 3 4]
2×2 Matrix{Float64}:
 1.0  2.0
 3.0  4.0

julia> findmin(A, dims=1)
([1.0 2.0], CartesianIndex{2}[CartesianIndex(1, 1) CartesianIndex(1, 2)])

julia> findmin(A, dims=2)
([1.0; 3.0;;], CartesianIndex{2}[CartesianIndex(1, 1); CartesianIndex(2, 1);;])
```
