```
svd!(A; full::Bool = false, alg::Algorithm = default_svd_alg(A)) -> SVD
```

`svd!` es lo mismo que [`svd`](@ref), pero ahorra espacio al sobrescribir la entrada `A`, en lugar de crear una copia. Consulta la documentación de [`svd`](@ref) para más detalles.
