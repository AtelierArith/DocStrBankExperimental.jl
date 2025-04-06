```
copy_adjoint!(B::AbstractVecOrMat, ir_dest::AbstractRange{Int}, jr_dest::AbstractRange{Int},
                A::AbstractVecOrMat, ir_src::AbstractRange{Int}, jr_src::AbstractRange{Int}) -> B
```

Copia eficientemente los elementos de la matriz `A` a `B` con adjunción de la siguiente manera:

```
B[ir_dest, jr_dest] = adjoint(A)[jr_src, ir_src]
```

Los elementos `B[ir_dest, jr_dest]` son sobrescritos. Además, los parámetros de rango de índice deben satisfacer `length(ir_dest) == length(jr_src)` y `length(jr_dest) == length(ir_src)`.
