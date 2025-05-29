```
matblock(mat_or_block; nlevel=2, tag="matblock(...)")
```

Create a [`GeneralMatrixBlock`](@ref) with a matrix `m`.

### Examples

```jldoctest; setup=:(using YaoBlocks)
julia> matblock(ComplexF64[0 1;1 0])
matblock(...)
```

!!!warn

```
Instead of converting it to the default data type `ComplexF64`,
this will return its contained matrix when calling `mat`.
```
