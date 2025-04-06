```
cos(A::AbstractMatrix)
```

Calcula el coseno de matriz de una matriz cuadrada `A`.

Si `A` es simétrica o hermítica, se utiliza su descomposición en valores propios ([`eigen`](@ref)) para calcular el coseno. De lo contrario, el coseno se determina llamando a [`exp`](@ref).

# Ejemplos

```jldoctest
julia> cos(fill(1.0, (2,2)))
2×2 Matrix{Float64}:
  0.291927  -0.708073
 -0.708073   0.291927
```
