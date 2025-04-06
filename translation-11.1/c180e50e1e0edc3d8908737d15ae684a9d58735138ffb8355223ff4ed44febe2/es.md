```
ftranspose!(X::AbstractSparseMatrixCSC{Tv,Ti}, A::AbstractSparseMatrixCSC{Tv,Ti}, f::Function) where {Tv,Ti}
```

Transponer `A` y almacenarlo en `X` mientras se aplica la función `f` a los elementos no nulos. No elimina los ceros creados por `f`. `size(X)` debe ser igual a `size(transpose(A))`. No se asigna memoria adicional más allá de redimensionar `rowval` y `nzval` de `X`, si es necesario.

Ver `halfperm!`
