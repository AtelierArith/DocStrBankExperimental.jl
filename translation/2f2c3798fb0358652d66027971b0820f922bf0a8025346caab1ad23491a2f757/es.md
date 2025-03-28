```
maximum(A::AbstractArray; dims)
```

Calcula el valor máximo de un array sobre las dimensiones dadas. Consulta también la función [`max(a,b)`](@ref) para obtener el máximo de dos o más argumentos, que se puede aplicar elemento por elemento a arrays a través de `max.(a,b)`.

Consulta también: [`maximum!`](@ref), [`extrema`](@ref), [`findmax`](@ref), [`argmax`](@ref).

# Ejemplos

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> maximum(A, dims=1)
1×2 Matrix{Int64}:
 3  4

julia> maximum(A, dims=2)
2×1 Matrix{Int64}:
 2
 4
```
