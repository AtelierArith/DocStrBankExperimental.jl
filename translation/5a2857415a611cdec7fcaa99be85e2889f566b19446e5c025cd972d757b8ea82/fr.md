```
spzeros([type,]m[,n])
```

Crée un vecteur sparse de longueur `m` ou une matrice sparse de taille `m x n`. Ce tableau sparse ne contiendra aucune valeur non nulle. Aucun stockage ne sera alloué pour les valeurs non nulles lors de la construction. Le type par défaut est [`Float64`](@ref) s'il n'est pas spécifié.

# Exemples

```jldoctest
julia> spzeros(3, 3)
3×3 SparseMatrixCSC{Float64, Int64} avec 0 entrées stockées :
  ⋅    ⋅    ⋅
  ⋅    ⋅    ⋅
  ⋅    ⋅    ⋅

julia> spzeros(Float32, 4)
4-élément SparseVector{Float32, Int64} avec 0 entrées stockées
```
