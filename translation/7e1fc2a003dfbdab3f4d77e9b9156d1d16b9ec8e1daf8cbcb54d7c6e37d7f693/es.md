```
givens(f::T, g::T, i1::Integer, i2::Integer) where {T} -> (G::Givens, r::T)
```

Calcula la rotación de Givens `G` y el escalar `r` tal que para cualquier vector `x` donde

```
x[i1] = f
x[i2] = g
```

el resultado de la multiplicación

```
y = G*x
```

tiene la propiedad de que

```
y[i1] = r
y[i2] = 0
```

Ver también [`LinearAlgebra.Givens`](@ref).
