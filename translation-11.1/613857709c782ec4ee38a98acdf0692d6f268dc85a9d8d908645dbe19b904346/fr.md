```
permutedims(v::AbstractVector)
```

Reshape le vecteur `v` en une matrice ligne `1 × length(v)`. Diffère de [`transpose`](@ref) en ce sens que l'opération n'est pas récursive, ce qui est particulièrement utile pour les tableaux de valeurs non numériques (où le `transpose` récursif pourrait provoquer une erreur).

# Exemples

Contrairement à `transpose`, `permutedims` peut être utilisé sur des vecteurs d'éléments non numériques arbitraires, tels que des chaînes de caractères :

```jldoctest
julia> permutedims(["a", "b", "c"])
1×3 Matrix{String}:
 "a"  "b"  "c"
```

Pour les vecteurs de nombres, `permutedims(v)` fonctionne de manière similaire à `transpose(v)`, sauf que le type de retour diffère (il utilise [`reshape`](@ref) plutôt qu'une vue `LinearAlgebra.Transpose`, bien que les deux partagent la mémoire avec le tableau original `v`) :

```jldoctest; setup = :(using LinearAlgebra)
julia> v = [1, 2, 3, 4]
4-element Vector{Int64}:
 1
 2
 3
 4

julia> p = permutedims(v)
1×4 Matrix{Int64}:
 1  2  3  4

julia> r = transpose(v)
1×4 transpose(::Vector{Int64}) with eltype Int64:
 1  2  3  4

julia> p == r
true

julia> typeof(r)
Transpose{Int64, Vector{Int64}}

julia> p[1] = 5; r[2] = 6; # muter p ou r change également v

julia> v # partage la mémoire avec p et r
4-element Vector{Int64}:
 5
 6
 3
 4
```

Cependant, `permutedims` produit des résultats qui diffèrent de `transpose` pour les vecteurs dont les éléments sont eux-mêmes des matrices numériques :

```jldoctest; setup = :(using LinearAlgebra)
julia> V = [[[1 2; 3 4]]; [[5 6; 7 8]]]
2-element Vector{Matrix{Int64}}:
 [1 2; 3 4]
 [5 6; 7 8]

julia> permutedims(V)
1×2 Matrix{Matrix{Int64}}:
 [1 2; 3 4]  [5 6; 7 8]

julia> transpose(V)
1×2 transpose(::Vector{Matrix{Int64}}) with eltype Transpose{Int64, Matrix{Int64}}:
 [1 3; 2 4]  [5 7; 6 8]
```
