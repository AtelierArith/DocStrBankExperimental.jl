```
cholesky!(A::AbstractMatrix, NoPivot(); check = true) -> Cholesky
```

Lo mismo que [`cholesky`](@ref), pero ahorra espacio al sobrescribir la entrada `A`, en lugar de crear una copia. Se lanza una excepción [`InexactError`](@ref) si la factorización produce un número que no se puede representar con el tipo de elemento de `A`, por ejemplo, para tipos enteros.

# Ejemplos

```jldoctest
julia> A = [1 2; 2 50]
2×2 Matrix{Int64}:
 1   2
 2  50

julia> cholesky!(A)
ERROR: InexactError: Int64(6.782329983125268)
Stacktrace:
[...]
```
