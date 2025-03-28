```
count([f=identity,] A::AbstractArray; dims=:)
```

Cuenta el número de elementos en `A` para los cuales `f` devuelve `true` sobre las dimensiones dadas.

!!! compat "Julia 1.5"
    La palabra clave `dims` se agregó en Julia 1.5.


!!! compat "Julia 1.6"
    La palabra clave `init` se agregó en Julia 1.6.


# Ejemplos

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> count(<=(2), A, dims=1)
1×2 Matrix{Int64}:
 1  1

julia> count(<=(2), A, dims=2)
2×1 Matrix{Int64}:
 2
 0
```
