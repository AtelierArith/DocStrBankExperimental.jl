```
Diagonal(A::AbstractMatrix)
```

Construit une matrice à partir de la diagonale principale de `A`. La matrice d'entrée `A` peut être rectangulaire, mais la sortie sera carrée.

# Exemples

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> D = Diagonal(A)
2×2 Diagonal{Int64, Vector{Int64}}:
 1  ⋅
 ⋅  4

julia> A = [1 2 3; 4 5 6]
2×3 Matrix{Int64}:
 1  2  3
 4  5  6

julia> Diagonal(A)
2×2 Diagonal{Int64, Vector{Int64}}:
 1  ⋅
 ⋅  5
```
