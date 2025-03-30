```
eigvals!(A::Union{SymTridiagonal, Hermitian, Symmetric}, irange::UnitRange) -> values
```

[`eigvals`](@ref) ile aynı, ancak bir kopya oluşturmak yerine girdi `A`'yı üst üste yazarak alan tasarrufu sağlar. `irange`, aramak için bir özdeğer *indisleri* aralığıdır - örneğin, 2. ile 8. özdeğerler.
