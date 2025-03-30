```
spzeros([type,]m[,n])
```

길이 `m`의 희소 벡터 또는 크기 `m x n`의 희소 행렬을 생성합니다. 이 희소 배열은 비영 값이 포함되지 않습니다. 생성 중에 비영 값에 대한 저장소는 할당되지 않습니다. 타입이 지정되지 않으면 기본값은 [`Float64`](@ref)입니다.

# 예제

```jldoctest
julia> spzeros(3, 3)
3×3 SparseMatrixCSC{Float64, Int64} with 0 stored entries:
  ⋅    ⋅    ⋅
  ⋅    ⋅    ⋅
  ⋅    ⋅    ⋅

julia> spzeros(Float32, 4)
4-element SparseVector{Float32, Int64} with 0 stored entries
```
