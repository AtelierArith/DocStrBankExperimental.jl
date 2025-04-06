```
copyto!(B::AbstractMatrix, ir_dest::AbstractUnitRange, jr_dest::AbstractUnitRange,
        tM::AbstractChar,
        M::AbstractVecOrMat, ir_src::AbstractUnitRange, jr_src::AbstractUnitRange) -> B
```

Matris `M`'nin elemanlarını `tM` karakter parametresine bağlı olarak `B`'ye verimli bir şekilde kopyalayın:

|  `tM` | Hedef                 | Kaynak                         |
| -----:|:--------------------- |:------------------------------ |
| `'N'` | `B[ir_dest, jr_dest]` | `M[ir_src, jr_src]`            |
| `'T'` | `B[ir_dest, jr_dest]` | `transpose(M)[ir_src, jr_src]` |
| `'C'` | `B[ir_dest, jr_dest]` | `adjoint(M)[ir_src, jr_src]`   |

Elemanlar `B[ir_dest, jr_dest]` üzerine yazılır. Ayrıca, indeks aralığı parametreleri `length(ir_dest) == length(ir_src)` ve `length(jr_dest) == length(jr_src)` koşulunu sağlamalıdır.

Ayrıca [`copy_transpose!`](@ref) ve [`copy_adjoint!`](@ref) ile de bakabilirsiniz.
