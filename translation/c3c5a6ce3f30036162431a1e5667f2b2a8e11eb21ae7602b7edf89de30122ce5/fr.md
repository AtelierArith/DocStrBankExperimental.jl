```
nonzeros(A)
```

Renvoie un vecteur des valeurs non nulles structurelles dans le tableau sparse `A`. Cela inclut les zéros qui sont explicitement stockés dans le tableau sparse. Le vecteur retourné pointe directement vers le stockage interne des non-zéros de `A`, et toute modification du vecteur retourné modifiera également `A`. Voir [`rowvals`](@ref) et [`nzrange`](@ref).

# Exemples

```jldoctest
julia> A = sparse(2I, 3, 3)
3×3 SparseMatrixCSC{Int64, Int64} avec 3 entrées stockées :
 2  ⋅  ⋅
 ⋅  2  ⋅
 ⋅  ⋅  2

julia> nonzeros(A)
3-element Vector{Int64}:
 2
 2
 2
```
