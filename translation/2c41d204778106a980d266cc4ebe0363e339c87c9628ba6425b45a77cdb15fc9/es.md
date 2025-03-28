```
tan(A::AbstractMatrix)
```

Calcula la tangente de matriz de una matriz cuadrada `A`.

Si `A` es simétrica o hermítica, se utiliza su descomposición en valores propios ([`eigen`](@ref)) para calcular la tangente. De lo contrario, la tangente se determina llamando a [`exp`](@ref).

# Ejemplos

```jldoctest
julia> tan(fill(1.0, (2,2)))
2×2 Matrix{Float64}:
 -1.09252  -1.09252
 -1.09252  -1.09252
```
