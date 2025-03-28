```
adjoint!(X::AbstractSparseMatrixCSC{Tv,Ti}, A::AbstractSparseMatrixCSC{Tv,Ti}) where {Tv,Ti}
```

Transpone la matriz `A` y almacena el adjunto de los elementos en la matriz `X`. `size(X)` debe ser igual a `size(transpose(A))`. No se asigna memoria adicional más que el redimensionamiento de `rowval` y `nzval` de `X`, si es necesario.

Consulta `halfperm!`
