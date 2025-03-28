```
givens(A::AbstractArray, i1::Integer, i2::Integer, j::Integer) -> (G::Givens, r)
```

Calcula la rotación de Givens `G` y el escalar `r` tal que el resultado de la multiplicación

```
B = G*A
```

tiene la propiedad de que

```
B[i1,j] = r
B[i2,j] = 0
```

Ver también [`LinearAlgebra.Givens`](@ref). ```
