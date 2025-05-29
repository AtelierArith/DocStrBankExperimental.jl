```
GeneralMatrixBlock{D, MT} <: PrimitiveBlock{D}
GeneralMatrixBlock{D}(m, n, A, tag="matblock(...)")
GeneralMatrixBlock(A; nlevel=2, tag="matblock(...)")
```

General matrix gate wraps a matrix operator to quantum gates. This is the most general form of a quantum gate.

### Arguments

  * `m` and `n` are the number of dits in row and column.
  * `A` is a matrix.
  * `tag` is the printed information.
  * `D` and `nlevel` are the number of levels in each qudit.
