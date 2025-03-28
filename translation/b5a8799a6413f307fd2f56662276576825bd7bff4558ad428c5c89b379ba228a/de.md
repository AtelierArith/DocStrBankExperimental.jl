```
copy_transpose!(B::AbstractMatrix, ir_dest::AbstractUnitRange, jr_dest::AbstractUnitRange,
                tM::AbstractChar,
                M::AbstractVecOrMat, ir_src::AbstractUnitRange, jr_src::AbstractUnitRange) -> B
```

Effizient Elemente der Matrix `M` nach `B` kopieren, bedingt durch den Zeichenparameter `tM`, wie folgt:

|  `tM` | Ziel                  | Quelle                         |
| -----:|:--------------------- |:------------------------------ |
| `'N'` | `B[ir_dest, jr_dest]` | `transpose(M)[jr_src, ir_src]` |
| `'T'` | `B[ir_dest, jr_dest]` | `M[jr_src, ir_src]`            |
| `'C'` | `B[ir_dest, jr_dest]` | `conj(M)[jr_src, ir_src]`      |

Die Elemente `B[ir_dest, jr_dest]` werden überschrieben. Darüber hinaus müssen die Indexbereichsparameter die Bedingung `length(ir_dest) == length(jr_src)` und `length(jr_dest) == length(ir_src)` erfüllen.

Siehe auch [`copyto!`](@ref) und [`copy_adjoint!`](@ref).
