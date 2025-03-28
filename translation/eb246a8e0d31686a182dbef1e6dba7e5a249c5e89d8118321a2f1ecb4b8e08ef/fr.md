```
minimum(A::AbstractArray; dims)
```

Calcule la valeur minimale d'un tableau sur les dimensions données. Voir aussi la fonction [`min(a,b)`](@ref) pour prendre le minimum de deux ou plusieurs arguments, qui peut être appliquée élément par élément aux tableaux via `min.(a,b)`.

Voir aussi : [`minimum!`](@ref), [`extrema`](@ref), [`findmin`](@ref), [`argmin`](@ref).

# Exemples

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
