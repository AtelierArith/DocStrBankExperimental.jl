```
svd!(A; full::Bool = false, alg::Algorithm = default_svd_alg(A)) -> SVD
```

`svd!` est identique à [`svd`](@ref), mais économise de l'espace en écrasant l'entrée `A`, au lieu de créer une copie. Voir la documentation de [`svd`](@ref) pour plus de détails.
