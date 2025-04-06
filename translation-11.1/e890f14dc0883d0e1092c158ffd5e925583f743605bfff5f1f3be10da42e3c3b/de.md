```
copyto!(B::AbstractMatrix, ir_dest::AbstractUnitRange, jr_dest::AbstractUnitRange,
        tM::AbstractChar,
        M::AbstractVecOrMat, ir_src::AbstractUnitRange, jr_src::AbstractUnitRange) -> B
```

Effizient Elemente der Matrix `M` nach `B` kopieren, abhängig vom Zeichenparameter `tM`, wie folgt:

|  `tM` | Ziel                  | Quelle                         |
| -----:|:--------------------- |:------------------------------ |
| `'N'` | `B[ir_dest, jr_dest]` | `M[ir_src, jr_src]`            |
| `'T'` | `B[ir_dest, jr_dest]` | `transpose(M)[ir_src, jr_src]` |
| `'C'` | `B[ir_dest, jr_dest]` | `adjoint(M)[ir_src, jr_src]`   |

Die Elemente `B[ir_dest, jr_dest]` werden überschrieben. Darüber hinaus müssen die Indexbereichsparameter die Bedingung `length(ir_dest) == length(ir_src)` und `length(jr_dest) == length(jr_src)` erfüllen.

Siehe auch [`copy_transpose!`](@ref) und [`copy_adjoint!`](@ref).
