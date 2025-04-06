```
givens(f::T, g::T, i1::Integer, i2::Integer) where {T} -> (G::Givens, r::T)
```

Berechnet die Givens-Rotation `G` und den Skalar `r`, so dass für jeden Vektor `x`, bei dem

```
x[i1] = f
x[i2] = g
```

das Ergebnis der Multiplikation

```
y = G*x
```

die Eigenschaft hat, dass

```
y[i1] = r
y[i2] = 0
```

Siehe auch [`LinearAlgebra.Givens`](@ref).
