```
matblock(mat_or_block; nlevel=2, tag="matblock(...)")
```

行列 `m` を持つ [`GeneralMatrixBlock`](@ref) を作成します。

### 例

```jldoctest; setup=:(using YaoBlocks)
julia> matblock(ComplexF64[0 1;1 0])
matblock(...)
```

!!!warn

```
デフォルトのデータ型 `ComplexF64` に変換するのではなく、
`mat` を呼び出すとその含まれている行列が返されます。
```
