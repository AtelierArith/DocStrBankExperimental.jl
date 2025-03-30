```
spdiagm(kv::Pair{<:Integer,<:AbstractVector}...)
spdiagm(m::Integer, n::Integer, kv::Pair{<:Integer,<:AbstractVector}...)
```

`Pair`의 벡터와 대각선으로부터 희소 대각 행렬을 구성합니다. 각 벡터 `kv.second`는 `kv.first` 대각선에 배치됩니다. 기본적으로 행렬은 정사각형이며 그 크기는 `kv`로부터 유추되지만, 필요에 따라 0으로 패딩된 비정사각형 크기 `m`×`n`을 첫 번째 인수로 `m,n`을 전달하여 지정할 수 있습니다.

# 예제

```jldoctest
julia> spdiagm(-1 => [1,2,3,4], 1 => [4,3,2,1])
5×5 SparseMatrixCSC{Int64, Int64} with 8 stored entries:
 ⋅  4  ⋅  ⋅  ⋅
 1  ⋅  3  ⋅  ⋅
 ⋅  2  ⋅  2  ⋅
 ⋅  ⋅  3  ⋅  1
 ⋅  ⋅  ⋅  4  ⋅
```
