```
sin(A::AbstractMatrix)
```

Calcula el seno de matriz de una matriz cuadrada `A`.

Si `A` es simétrica o hermitiana, se utiliza su descomposición en valores propios ([`eigen`](@ref)) para calcular el seno. De lo contrario, el seno se determina llamando a [`exp`](@ref).

# Ejemplos

```jldoctest
julia> sin(fill(1.0, (2,2)))
2×2 Matrix{Float64}:
 0.454649  0.454649
 0.454649  0.454649
```
