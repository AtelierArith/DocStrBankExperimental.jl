```
copy_transpose!(B::AbstractMatrix, ir_dest::AbstractUnitRange, jr_dest::AbstractUnitRange,
                tM::AbstractChar,
                M::AbstractVecOrMat, ir_src::AbstractUnitRange, jr_src::AbstractUnitRange) -> B
```

Copia eficientemente los elementos de la matriz `M` a `B` condicionado al parámetro de carácter `tM` de la siguiente manera:

|  `tM` | Destino               | Fuente                         |
| -----:|:--------------------- |:------------------------------ |
| `'N'` | `B[ir_dest, jr_dest]` | `transpose(M)[jr_src, ir_src]` |
| `'T'` | `B[ir_dest, jr_dest]` | `M[jr_src, ir_src]`            |
| `'C'` | `B[ir_dest, jr_dest]` | `conj(M)[jr_src, ir_src]`      |

Los elementos `B[ir_dest, jr_dest]` son sobrescritos. Además, los parámetros de rango de índice deben satisfacer `length(ir_dest) == length(jr_src)` y `length(jr_dest) == length(ir_src)`.

Consulta también [`copyto!`](@ref) y [`copy_adjoint!`](@ref).
