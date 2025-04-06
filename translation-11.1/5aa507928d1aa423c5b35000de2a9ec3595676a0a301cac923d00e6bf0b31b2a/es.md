```
median(A::AbstractArray; dims)
```

Calcula la mediana de un arreglo a lo largo de las dimensiones dadas.

# Ejemplos

```jldoctest
julia> using Statistics

julia> median([1 2; 3 4], dims=1)
1×2 Matrix{Float64}:
 2.0  3.0
```
