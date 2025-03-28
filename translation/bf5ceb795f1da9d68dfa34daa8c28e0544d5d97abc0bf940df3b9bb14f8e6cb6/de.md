```
givens(x::AbstractVector, i1::Integer, i2::Integer) -> (G::Givens, r)
```

Berechnet die Givens-Rotation `G` und den Skalar `r`, so dass das Ergebnis der Multiplikation

```
B = G*x
```

die Eigenschaft hat, dass

```
B[i1] = r
B[i2] = 0
```

Siehe auch [`LinearAlgebra.Givens`](@ref). ```
