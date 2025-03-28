```
givens(x::AbstractVector, i1::Integer, i2::Integer) -> (G::Givens, r)
```

Calcula la rotación de Givens `G` y el escalar `r` tal que el resultado de la multiplicación

```
B = G*x
```

tiene la propiedad de que

```
B[i1] = r
B[i2] = 0
```

Ver también [`LinearAlgebra.Givens`](@ref). ```
