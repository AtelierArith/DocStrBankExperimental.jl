```
cholesky!(A::AbstractMatrix, RowMaximum(); tol = 0.0, check = true) -> CholeskyPivoted
```

[`cholesky`](@ref) ile aynı, ancak bir kopya oluşturmak yerine girdi `A`'yı üst üste yazarak alan tasarrufu sağlar. Faktörizasyon, `A`'nın eleman türü tarafından temsil edilemeyen bir sayı üretirse, örneğin tam sayı türleri için, bir [`InexactError`](@ref) istisnası fırlatılır.
