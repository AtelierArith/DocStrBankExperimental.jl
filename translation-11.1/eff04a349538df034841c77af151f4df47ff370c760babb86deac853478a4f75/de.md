```
givens(A::AbstractArray, i1::Integer, i2::Integer, j::Integer) -> (G::Givens, r)
```

Berechnet die Givens-Rotation `G` und den Skalar `r`, so dass das Ergebnis der Multiplikation

```
B = G*A
```

die Eigenschaft hat, dass

```
B[i1,j] = r
B[i2,j] = 0
```

Siehe auch [`LinearAlgebra.Givens`](@ref). ```
