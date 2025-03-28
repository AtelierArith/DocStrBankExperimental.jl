```
popat!(a::Vector, i::Integer, [default])
```

Elimina el elemento en el índice dado `i` y lo devuelve. Los elementos subsiguientes se desplazan para llenar el hueco resultante. Cuando `i` no es un índice válido para `a`, devuelve `default`, o lanza un error si `default` no está especificado.

Véase también: [`pop!`](@ref), [`popfirst!`](@ref), [`deleteat!`](@ref), [`splice!`](@ref).

!!! compat "Julia 1.5"
    Esta función está disponible desde Julia 1.5.


# Ejemplos

```jldoctest
julia> a = [4, 3, 2, 1]; popat!(a, 2)
3

julia> a
Vector{Int64} de 3 elementos:
 4
 2
 1

julia> popat!(a, 4, missing)
missing

julia> popat!(a, 4)
ERROR: BoundsError: intento de acceder a Vector{Int64} de 3 elementos en el índice [4]
[...]
```
