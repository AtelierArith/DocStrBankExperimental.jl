```
copy_adjoint!(B::AbstractVecOrMat, ir_dest::AbstractRange{Int}, jr_dest::AbstractRange{Int},
                A::AbstractVecOrMat, ir_src::AbstractRange{Int}, jr_src::AbstractRange{Int}) -> B
```

Copier efficacement les éléments de la matrice `A` vers `B` avec adjunction comme suit :

```
B[ir_dest, jr_dest] = adjoint(A)[jr_src, ir_src]
```

Les éléments `B[ir_dest, jr_dest]` sont écrasés. De plus, les paramètres de plage d'index doivent satisfaire `length(ir_dest) == length(jr_src)` et `length(jr_dest) == length(ir_src)`.
