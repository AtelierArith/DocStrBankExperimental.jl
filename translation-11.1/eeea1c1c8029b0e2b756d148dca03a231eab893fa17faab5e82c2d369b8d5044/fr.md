```
SparseVector{Tv,Ti<:Integer} <: AbstractSparseVector{Tv,Ti}
```

Type de vecteur pour stocker des vecteurs creux. Peut être créé en passant la longueur du vecteur, un vecteur *trié* d'indices non nuls, et un vecteur de valeurs non nulles.

Par exemple, le vecteur `[5, 6, 0, 7]` peut être représenté comme

```julia
SparseVector(4, [1, 2, 4], [5, 6, 7])
```

Cela indique que l'élément à l'index 1 est 5, à l'index 2 est 6, à l'index 3 est `zero(Int)`, et à l'index 4 est 7.

Il peut être plus pratique de créer des vecteurs creux directement à partir de vecteurs denses en utilisant `sparse` comme

```julia
sparse([5, 6, 0, 7])
```

produit le même vecteur creux.
