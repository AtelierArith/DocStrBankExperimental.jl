```
copy_adjoint!(B::AbstractVecOrMat, ir_dest::AbstractRange{Int}, jr_dest::AbstractRange{Int},
                A::AbstractVecOrMat, ir_src::AbstractRange{Int}, jr_src::AbstractRange{Int}) -> B
```

Effizient Elemente der Matrix `A` nach `B` mit Adjunktion wie folgt kopieren:

```
B[ir_dest, jr_dest] = adjoint(A)[jr_src, ir_src]
```

Die Elemente `B[ir_dest, jr_dest]` werden überschrieben. Darüber hinaus müssen die Indexbereichsparameter `length(ir_dest) == length(jr_src)` und `length(jr_dest) == length(ir_src)` erfüllen.
