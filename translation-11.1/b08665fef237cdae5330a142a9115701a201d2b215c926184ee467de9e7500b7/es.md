```
qr!(A, pivot = NoPivot(); blocksize)
```

`qr!` es lo mismo que [`qr`](@ref) cuando `A` es un subtipo de [`AbstractMatrix`](@ref), pero ahorra espacio al sobrescribir la entrada `A`, en lugar de crear una copia. Se lanza una excepción [`InexactError`](@ref) si la factorización produce un número que no es representable por el tipo de elemento de `A`, por ejemplo, para tipos enteros.

!!! compat "Julia 1.4"
    El argumento de palabra clave `blocksize` requiere Julia 1.4 o posterior.


# Ejemplos

```jldoctest
julia> a = [1. 2.; 3. 4.]
2×2 Matrix{Float64}:
 1.0  2.0
 3.0  4.0

julia> qr!(a)
LinearAlgebra.QRCompactWY{Float64, Matrix{Float64}, Matrix{Float64}}
Q factor: 2×2 LinearAlgebra.QRCompactWYQ{Float64, Matrix{Float64}, Matrix{Float64}}
R factor:
2×2 Matrix{Float64}:
 -3.16228  -4.42719
  0.0      -0.632456

julia> a = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> qr!(a)
ERROR: InexactError: Int64(3.1622776601683795)
Stacktrace:
[...]
```
