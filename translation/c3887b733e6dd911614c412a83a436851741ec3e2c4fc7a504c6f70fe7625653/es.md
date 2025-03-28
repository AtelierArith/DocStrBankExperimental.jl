```
lu!(A, pivot = RowMaximum(); check = true, allowsingular = false) -> LU
```

`lu!` es lo mismo que [`lu`](@ref), pero ahorra espacio al sobrescribir la entrada `A`, en lugar de crear una copia. Se lanza una excepción [`InexactError`](@ref) si la factorización produce un número que no es representable por el tipo de elemento de `A`, por ejemplo, para tipos enteros.

!!! compat "Julia 1.11"
    El argumento de palabra clave `allowsingular` se agregó en Julia 1.11.


# Ejemplos

```jldoctest
julia> A = [4. 3.; 6. 3.]
2×2 Matrix{Float64}:
 4.0  3.0
 6.0  3.0

julia> F = lu!(A)
LU{Float64, Matrix{Float64}, Vector{Int64}}
L factor:
2×2 Matrix{Float64}:
 1.0       0.0
 0.666667  1.0
U factor:
2×2 Matrix{Float64}:
 6.0  3.0
 0.0  1.0

julia> iA = [4 3; 6 3]
2×2 Matrix{Int64}:
 4  3
 6  3

julia> lu!(iA)
ERROR: InexactError: Int64(0.6666666666666666)
Stacktrace:
[...]
```
