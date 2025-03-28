```
StridedArray{T, N}
```

Un [`Union`](@ref) codé en dur des types de tableau courants qui suivent l' [interface de tableau stridé](@ref man-interface-strided-arrays), avec des éléments de type `T` et `N` dimensions.

Si `A` est un `StridedArray`, alors ses éléments sont stockés en mémoire avec des décalages, qui peuvent varier entre les dimensions mais sont constants au sein d'une dimension. Par exemple, `A` pourrait avoir un pas de 2 dans la dimension 1, et un pas de 3 dans la dimension 2. Incrémenter `A` le long de la dimension `d` saute en mémoire de [`stride(A, d)`] emplacements. Les tableaux stridés sont particulièrement importants et utiles car ils peuvent parfois être passés directement comme pointeurs à des bibliothèques de langages étrangers comme BLAS.
