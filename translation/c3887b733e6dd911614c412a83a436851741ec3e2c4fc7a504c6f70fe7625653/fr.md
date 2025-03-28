```
lu!(A, pivot = RowMaximum(); check = true, allowsingular = false) -> LU
```

`lu!` est identique à [`lu`](@ref), mais économise de l'espace en écrasant l'entrée `A`, au lieu de créer une copie. Une exception [`InexactError`](@ref) est levée si la factorisation produit un nombre non représentable par le type d'élément de `A`, par exemple pour les types entiers.

!!! compat "Julia 1.11"
    L'argument clé `allowsingular` a été ajouté dans Julia 1.11.


# Exemples

```jldoctest
julia> A = [4. 3.; 6. 3.]
2×2 Matrix{Float64}:
 4.0  3.0
 6.0  3.0

julia> F = lu!(A)
LU{Float64, Matrix{Float64}, Vector{Int64}}
Facteur L :
2×2 Matrix{Float64}:
 1.0       0.0
 0.666667  1.0
Facteur U :
2×2 Matrix{Float64}:
 6.0  3.0
 0.0  1.0

julia> iA = [4 3; 6 3]
2×2 Matrix{Int64}:
 4  3
 6  3

julia> lu!(iA)
ERREUR: InexactError: Int64(0.6666666666666666)
Trace de la pile :
[...]
```
