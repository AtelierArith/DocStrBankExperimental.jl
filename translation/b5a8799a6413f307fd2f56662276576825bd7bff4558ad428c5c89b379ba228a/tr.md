```
copy_transpose!(B::AbstractMatrix, ir_dest::AbstractUnitRange, jr_dest::AbstractUnitRange,
                tM::AbstractChar,
                M::AbstractVecOrMat, ir_src::AbstractUnitRange, jr_src::AbstractUnitRange) -> B
```

Matris `M`'nin elemanlarını `B`'ye, karakter parametresi `tM`'ye bağlı olarak verimli bir şekilde kopyalayın:

|  `tM` | Hedef                 | Kaynak                         |
| -----:|:--------------------- |:------------------------------ |
| `'N'` | `B[ir_dest, jr_dest]` | `transpose(M)[jr_src, ir_src]` |
| `'T'` | `B[ir_dest, jr_dest]` | `M[jr_src, ir_src]`            |
| `'C'` | `B[ir_dest, jr_dest]` | `conj(M)[jr_src, ir_src]`      |

Elemanlar `B[ir_dest, jr_dest]` üzerine yazılır. Ayrıca, indeks aralığı parametreleri `length(ir_dest) == length(jr_src)` ve `length(jr_dest) == length(ir_src)` koşulunu sağlamalıdır.

Ayrıca [`copyto!`](@ref) ve [`copy_adjoint!`](@ref) ile de bakabilirsiniz.
