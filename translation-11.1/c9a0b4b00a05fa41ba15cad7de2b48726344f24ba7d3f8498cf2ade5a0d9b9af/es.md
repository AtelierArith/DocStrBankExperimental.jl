```
reverse(A; dims=:)
```

Invierte `A` a lo largo de la dimensión `dims`, que puede ser un entero (una sola dimensión), una tupla de enteros (una tupla de dimensiones) o `:` (invertir a lo largo de todas las dimensiones, el valor predeterminado). Consulta también [`reverse!`](@ref) para la inversión en su lugar.

# Ejemplos

```jldoctest
julia> b = Int64[1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> reverse(b, dims=2)
2×2 Matrix{Int64}:
 2  1
 4  3

julia> reverse(b)
2×2 Matrix{Int64}:
 4  3
 2  1
```

!!! compat "Julia 1.6"
    Antes de Julia 1.6, solo se admiten `dims` de un solo entero en `reverse`.

