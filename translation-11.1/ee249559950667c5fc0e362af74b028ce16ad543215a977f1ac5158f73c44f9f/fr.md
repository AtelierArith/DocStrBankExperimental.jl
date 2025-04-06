```
reshape(A, dims...) -> AbstractArray
reshape(A, dims) -> AbstractArray
```

Renvoie un tableau avec les mêmes données que `A`, mais avec des tailles de dimensions ou un nombre de dimensions différents. Les deux tableaux partagent les mêmes données sous-jacentes, de sorte que le résultat est mutable si et seulement si `A` est mutable, et que la modification des éléments de l'un altère les valeurs de l'autre.

Les nouvelles dimensions peuvent être spécifiées soit sous forme d'une liste d'arguments, soit sous forme d'un tuple de forme. Au maximum une dimension peut être spécifiée avec un `:`, auquel cas sa longueur est calculée de sorte que son produit avec toutes les dimensions spécifiées soit égal à la longueur du tableau original `A`. Le nombre total d'éléments ne doit pas changer.

# Exemples

```jldoctest
julia> A = Vector(1:16)
16-element Vector{Int64}:
  1
  2
  3
  4
  5
  6
  7
  8
  9
 10
 11
 12
 13
 14
 15
 16

julia> reshape(A, (4, 4))
4×4 Matrix{Int64}:
 1  5   9  13
 2  6  10  14
 3  7  11  15
 4  8  12  16

julia> reshape(A, 2, :)
2×8 Matrix{Int64}:
 1  3  5  7   9  11  13  15
 2  4  6  8  10  12  14  16

julia> reshape(1:6, 2, 3)
2×3 reshape(::UnitRange{Int64}, 2, 3) with eltype Int64:
 1  3  5
 2  4  6
```
