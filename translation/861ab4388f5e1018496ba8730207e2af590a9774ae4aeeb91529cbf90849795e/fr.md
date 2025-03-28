```
permutedims(A::AbstractArray, perm)
permutedims(A::AbstractMatrix)
```

Permute les dimensions (axes) du tableau `A`. `perm` est un tuple ou un vecteur de `ndims(A)` entiers spécifiant la permutation.

Si `A` est un tableau 2d ([`AbstractMatrix`](@ref)), alors `perm` par défaut est `(2,1)`, échangeant les deux axes de `A` (les lignes et les colonnes de la matrice). Cela diffère de [`transpose`](@ref) en ce sens que l'opération n'est pas récursive, ce qui est particulièrement utile pour les tableaux de valeurs non numériques (où le `transpose` récursif provoquerait une erreur) et/ou les tableaux 2d qui ne représentent pas des opérateurs linéaires.

Pour les tableaux 1d, voir [`permutedims(v::AbstractVector)`](@ref), qui retourne une "matrice" à 1 ligne.

Voir aussi [`permutedims!`](@ref), [`PermutedDimsArray`](@ref), [`transpose`](@ref), [`invperm`](@ref).

# Exemples

## Tableaux 2d :

Contrairement à `transpose`, `permutedims` peut être utilisé pour échanger les lignes et les colonnes de tableaux 2d d'éléments non numériques arbitraires, tels que des chaînes :

```jldoctest
julia> A = ["a" "b" "c"
            "d" "e" "f"]
2×3 Matrix{String}:
 "a"  "b"  "c"
 "d"  "e"  "f"

julia> permutedims(A)
3×2 Matrix{String}:
 "a"  "d"
 "b"  "e"
 "c"  "f"
```

Et `permutedims` produit des résultats qui diffèrent de `transpose` pour les matrices dont les éléments sont eux-mêmes des matrices numériques :

```jldoctest; setup = :(using LinearAlgebra)
julia> a = [1 2; 3 4];

julia> b = [5 6; 7 8];

julia> c = [9 10; 11 12];

julia> d = [13 14; 15 16];

julia> X = [[a] [b]; [c] [d]]
2×2 Matrix{Matrix{Int64}}:
 [1 2; 3 4]     [5 6; 7 8]
 [9 10; 11 12]  [13 14; 15 16]

julia> permutedims(X)
2×2 Matrix{Matrix{Int64}}:
 [1 2; 3 4]  [9 10; 11 12]
 [5 6; 7 8]  [13 14; 15 16]

julia> transpose(X)
2×2 transpose(::Matrix{Matrix{Int64}}) with eltype Transpose{Int64, Matrix{Int64}}:
 [1 3; 2 4]  [9 11; 10 12]
 [5 7; 6 8]  [13 15; 14 16]
```

## Tableaux multi-dimensionnels

```jldoctest
julia> A = reshape(Vector(1:8), (2,2,2))
2×2×2 Array{Int64, 3}:
[:, :, 1] =
 1  3
 2  4

[:, :, 2] =
 5  7
 6  8

julia> perm = (3, 1, 2); # mettre la dernière dimension en premier

julia> B = permutedims(A, perm)
2×2×2 Array{Int64, 3}:
[:, :, 1] =
 1  2
 5  6

[:, :, 2] =
 3  4
 7  8

julia> A == permutedims(B, invperm(perm)) # la permutation inverse
true
```

Pour chaque dimension `i` de `B = permutedims(A, perm)`, sa dimension correspondante de `A` sera `perm[i]`. Cela signifie que l'égalité `size(B, i) == size(A, perm[i])` est vraie.

```jldoctest
julia> A = randn(5, 7, 11, 13);

julia> perm = [4, 1, 3, 2];

julia> B = permutedims(A, perm);

julia> size(B)
(13, 5, 11, 7)

julia> size(A)[perm] == ans
true
```
