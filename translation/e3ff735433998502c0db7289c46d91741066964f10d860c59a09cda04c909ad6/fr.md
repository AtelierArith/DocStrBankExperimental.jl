```
hvncat(dim::Int, row_first, values...)
hvncat(dims::Tuple{Vararg{Int}}, row_first, values...)
hvncat(shape::Tuple{Vararg{Tuple}}, row_first, values...)
```

Concaténation horizontale, verticale et n-dimensionnelle de plusieurs `values` en un seul appel.

Cette fonction est appelée pour la syntaxe de matrice bloc. Le premier argument spécifie soit la forme de la concaténation, similaire à `hvcat`, sous forme de tuple de tuples, soit les dimensions qui spécifient le nombre clé d'éléments le long de chaque axe, et est utilisé pour déterminer les dimensions de sortie. La forme `dims` est plus performante et est utilisée par défaut lorsque l'opération de concaténation a le même nombre d'éléments le long de chaque axe (par exemple, [a b; c d;;; e f ; g h]). La forme `shape` est utilisée lorsque le nombre d'éléments le long de chaque axe est déséquilibré (par exemple, [a b ; c]). La syntaxe déséquilibrée nécessite une surcharge de validation supplémentaire. La forme `dim` est une optimisation pour la concaténation le long d'une seule dimension. `row_first` indique comment les `values` sont ordonnés. La signification des premier et deuxième éléments de `shape` est également échangée en fonction de `row_first`.

# Exemples

```jldoctest
julia> a, b, c, d, e, f = 1, 2, 3, 4, 5, 6
(1, 2, 3, 4, 5, 6)

julia> [a b c;;; d e f]
1×3×2 Array{Int64, 3}:
[:, :, 1] =
 1  2  3

[:, :, 2] =
 4  5  6

julia> hvncat((2,1,3), false, a,b,c,d,e,f)
2×1×3 Array{Int64, 3}:
[:, :, 1] =
 1
 2

[:, :, 2] =
 3
 4

[:, :, 3] =
 5
 6

julia> [a b;;; c d;;; e f]
1×2×3 Array{Int64, 3}:
[:, :, 1] =
 1  2

[:, :, 2] =
 3  4

[:, :, 3] =
 5  6

julia> hvncat(((3, 3), (3, 3), (6,)), true, a, b, c, d, e, f)
1×3×2 Array{Int64, 3}:
[:, :, 1] =
 1  2  3

[:, :, 2] =
 4  5  6
```

# Exemples pour la construction des arguments

```
[a b c ; d e f ;;;
 g h i ; j k l ;;;
 m n o ; p q r ;;;
 s t u ; v w x]
⇒ dims = (2, 3, 4)

[a b ; c ;;; d ;;;;]
 ___   _     _
 2     1     1 = éléments dans chaque ligne (2, 1, 1)
 _______     _
 3           1 = éléments dans chaque colonne (3, 1)
 _____________
 4             = éléments dans chaque tranche 3d (4,)
 _____________
 4             = éléments dans chaque tranche 4d (4,)
⇒ shape = ((2, 1, 1), (3, 1), (4,), (4,)) avec `row_first` = true
```
