```
copy_transpose!(B::AbstractMatrix, ir_dest::AbstractUnitRange, jr_dest::AbstractUnitRange,
                tM::AbstractChar,
                M::AbstractVecOrMat, ir_src::AbstractUnitRange, jr_src::AbstractUnitRange) -> B
```

Copier efficacement les éléments de la matrice `M` vers `B` en fonction du paramètre de caractère `tM` comme suit :

|  `tM` | Destination           | Source                         |
| -----:|:--------------------- |:------------------------------ |
| `'N'` | `B[ir_dest, jr_dest]` | `transpose(M)[jr_src, ir_src]` |
| `'T'` | `B[ir_dest, jr_dest]` | `M[jr_src, ir_src]`            |
| `'C'` | `B[ir_dest, jr_dest]` | `conj(M)[jr_src, ir_src]`      |

Les éléments `B[ir_dest, jr_dest]` sont écrasés. De plus, les paramètres de plage d'index doivent satisfaire `length(ir_dest) == length(jr_src)` et `length(jr_dest) == length(ir_src)`.

Voir aussi [`copyto!`](@ref) et [`copy_adjoint!`](@ref).
