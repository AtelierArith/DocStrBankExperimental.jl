```
givens(A::AbstractArray, i1::Integer, i2::Integer, j::Integer) -> (G::Givens, r)
```

Calcule la rotation de Givens `G` et le scalaire `r` tels que le résultat de la multiplication

```
B = G*A
```

a la propriété que

```
B[i1,j] = r
B[i2,j] = 0
```

Voir aussi [`LinearAlgebra.Givens`](@ref). ```
