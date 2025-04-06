```
rowvals(A::AbstractSparseMatrixCSC)
```

Renvoie un vecteur des indices de ligne de `A`. Toute modification du vecteur retourné modifiera également `A`. Fournir un accès à la façon dont les indices de ligne sont stockés en interne peut être utile en conjonction avec l'itération sur les valeurs non nulles structurelles. Voir aussi [`nonzeros`](@ref) et [`nzrange`](@ref).

# Exemples

```jldoctest
julia> A = sparse(2I, 3, 3)
3×3 SparseMatrixCSC{Int64, Int64} avec 3 entrées stockées :
 2  ⋅  ⋅
 ⋅  2  ⋅
 ⋅  ⋅  2

julia> rowvals(A)
3-element Vector{Int64}:
 1
 2
 3
```
