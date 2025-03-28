```
reinterpret(reshape, T, A::AbstractArray{S}) -> B
```

Changez l'interprétation de type de `A` tout en consommant ou en ajoutant une "dimension de canal."

Si `sizeof(T) = n*sizeof(S)` pour `n>1`, la première dimension de `A` doit avoir une taille de `n` et `B` n'a pas la première dimension de `A`. Inversement, si `sizeof(S) = n*sizeof(T)` pour `n>1`, `B` obtient une nouvelle première dimension de taille `n`. La dimensionnalité reste inchangée si `sizeof(T) == sizeof(S)`.

!!! compat "Julia 1.6"
    Cette méthode nécessite au moins Julia 1.6.


# Exemples

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> reinterpret(reshape, Complex{Int}, A)    # le résultat est un vecteur
2-element reinterpret(reshape, Complex{Int64}, ::Matrix{Int64}) with eltype Complex{Int64}:
 1 + 3im
 2 + 4im

julia> a = [(1,2,3), (4,5,6)]
2-element Vector{Tuple{Int64, Int64, Int64}}:
 (1, 2, 3)
 (4, 5, 6)

julia> reinterpret(reshape, Int, a)             # le résultat est une matrice
3×2 reinterpret(reshape, Int64, ::Vector{Tuple{Int64, Int64, Int64}}) with eltype Int64:
 1  4
 2  5
 3  6
```
