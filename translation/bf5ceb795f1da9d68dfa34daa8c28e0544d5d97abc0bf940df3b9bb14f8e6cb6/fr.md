```
givens(x::AbstractVector, i1::Integer, i2::Integer) -> (G::Givens, r)
```

Calcule la rotation de Givens `G` et le scalaire `r` de sorte que le résultat de la multiplication

```
B = G*x
```

ait la propriété que

```
B[i1] = r
B[i2] = 0
```

Voir aussi [`LinearAlgebra.Givens`](@ref). ```
