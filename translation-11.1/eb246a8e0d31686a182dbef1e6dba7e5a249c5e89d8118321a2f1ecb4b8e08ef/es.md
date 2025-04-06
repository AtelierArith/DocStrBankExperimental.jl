```
minimum(A::AbstractArray; dims)
```

Calcula el valor mínimo de un array sobre las dimensiones dadas. Véase también la función [`min(a,b)`](@ref) para tomar el mínimo de dos o más argumentos, que se puede aplicar elemento a elemento a arrays a través de `min.(a,b)`.

Véase también: [`minimum!`](@ref), [`extrema`](@ref), [`findmin`](@ref), [`argmin`](@ref).

# Ejemplos

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> minimum(A, dims=1)
1×2 Matrix{Int64}:
 1  2

julia> minimum(A, dims=2)
2×1 Matrix{Int64}:
 1
 3
```
