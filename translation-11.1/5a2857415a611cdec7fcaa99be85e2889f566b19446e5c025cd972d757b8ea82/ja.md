```
spzeros([type,]m[,n])
```

長さ `m` の疎ベクトルまたはサイズ `m x n` の疎行列を作成します。この疎配列には非ゼロ値は含まれません。構築中に非ゼロ値のためのストレージは割り当てられません。タイプが指定されていない場合、デフォルトは [`Float64`](@ref) です。

# 例

```jldoctest
julia> spzeros(3, 3)
3×3 SparseMatrixCSC{Float64, Int64} with 0 stored entries:
  ⋅    ⋅    ⋅
  ⋅    ⋅    ⋅
  ⋅    ⋅    ⋅

julia> spzeros(Float32, 4)
4-element SparseVector{Float32, Int64} with 0 stored entries
```
