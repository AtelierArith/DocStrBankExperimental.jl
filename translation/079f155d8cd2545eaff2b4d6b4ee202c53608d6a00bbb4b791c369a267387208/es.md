```
transpose!(X::AbstractSparseMatrixCSC{Tv,Ti}, A::AbstractSparseMatrixCSC{Tv,Ti}) donde {Tv,Ti}
```

Transpone la matriz `A` y la almacena en la matriz `X`. `size(X)` debe ser igual a `size(transpose(A))`. No se asigna memoria adicional más allá de redimensionar `rowval` y `nzval` de `X`, si es necesario.

Consulta `halfperm!`
