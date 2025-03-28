```
maximum(A::AbstractArray; dims)
```

Calcule la valeur maximale d'un tableau sur les dimensions données. Voir aussi la fonction [`max(a,b)`](@ref) pour prendre le maximum de deux ou plusieurs arguments, qui peut être appliquée élément par élément aux tableaux via `max.(a,b)`.

Voir aussi : [`maximum!`](@ref), [`extrema`](@ref), [`findmax`](@ref), [`argmax`](@ref).

# Exemples

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
