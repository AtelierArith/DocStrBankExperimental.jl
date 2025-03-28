```
sortslices(A; dims, alg::Algorithm=DEFAULT_UNSTABLE, lt=isless, by=identity, rev::Bool=false, order::Ordering=Forward)
```

Trie les tranches d'un tableau `A`. L'argument clé requis `dims` doit être soit un entier, soit un tuple d'entiers. Il spécifie la ou les dimensions sur lesquelles les tranches sont triées.

Par exemple, si `A` est une matrice, `dims=1` triera les lignes, `dims=2` triera les colonnes. Notez que la fonction de comparaison par défaut sur les tranches unidimensionnelles trie de manière lexicographique.

Pour les autres arguments clés, voir la documentation de [`sort!`](@ref).

# Exemples

```jldoctest
julia> sortslices([7 3 5; -1 6 4; 9 -2 8], dims=1) # Trier les lignes
3×3 Matrix{Int64}:
 -1   6  4
  7   3  5
  9  -2  8

julia> sortslices([7 3 5; -1 6 4; 9 -2 8], dims=1, lt=(x,y)->isless(x[2],y[2]))
3×3 Matrix{Int64}:
  9  -2  8
  7   3  5
 -1   6  4

julia> sortslices([7 3 5; -1 6 4; 9 -2 8], dims=1, rev=true)
3×3 Matrix{Int64}:
  9  -2  8
  7   3  5
 -1   6  4

julia> sortslices([7 3 5; 6 -1 -4; 9 -2 8], dims=2) # Trier les colonnes
3×3 Matrix{Int64}:
  3   5  7
 -1  -4  6
 -2   8  9

julia> sortslices([7 3 5; 6 -1 -4; 9 -2 8], dims=2, alg=InsertionSort, lt=(x,y)->isless(x[2],y[2]))
3×3 Matrix{Int64}:
  5   3  7
 -4  -1  6
  8  -2  9

julia> sortslices([7 3 5; 6 -1 -4; 9 -2 8], dims=2, rev=true)
3×3 Matrix{Int64}:
 7   5   3
 6  -4  -1
 9   8  -2
```

# Dimensions supérieures

`sortslices` s'étend naturellement aux dimensions supérieures. Par exemple, si `A` est un tableau 2x2x2, `sortslices(A, dims=3)` triera les tranches dans la 3ème dimension, passant les tranches 2x2 `A[:, :, 1]` et `A[:, :, 2]` à la fonction de comparaison. Notez que bien qu'il n'y ait pas d'ordre par défaut sur les tranches de dimensions supérieures, vous pouvez utiliser l'argument clé `by` ou `lt` pour spécifier un tel ordre.

Si `dims` est un tuple, l'ordre des dimensions dans `dims` est pertinent et spécifie l'ordre linéaire des tranches. Par exemple, si `A` est tridimensionnel et que `dims` est `(1, 2)`, les ordres des deux premières dimensions sont réarrangés de sorte que les tranches (de la troisième dimension restante) soient triées. Si `dims` est `(2, 1)` à la place, les mêmes tranches seront prises, mais l'ordre du résultat sera de type "row-major".

# Exemples de dimensions supérieures

```
julia> A = [4 3; 2 1 ;;; 'A' 'B'; 'C' 'D']
2×2×2 Array{Any, 3}:
[:, :, 1] =
 4  3
 2  1

[:, :, 2] =
 'A'  'B'
 'C'  'D'

julia> sortslices(A, dims=(1,2))
2×2×2 Array{Any, 3}:
[:, :, 1] =
 1  3
 2  4

[:, :, 2] =
 'D'  'B'
 'C'  'A'

julia> sortslices(A, dims=(2,1))
2×2×2 Array{Any, 3}:
[:, :, 1] =
 1  2
 3  4

[:, :, 2] =
 'D'  'C'
 'B'  'A'

julia> sortslices(reshape([5; 4; 3; 2; 1], (1,1,5)), dims=3, by=x->x[1,1])
1×1×5 Array{Int64, 3}:
[:, :, 1] =
 1

[:, :, 2] =
 2

[:, :, 3] =
 3

[:, :, 4] =
 4

[:, :, 5] =
 5
```
