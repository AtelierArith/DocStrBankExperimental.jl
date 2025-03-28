```
UnitRange{T<:Real}
```

Un rango parametrizado por un `start` y `stop` de tipo `T`, lleno de elementos espaciados por `1` desde `start` hasta que se exceda `stop`. La sintaxis `a:b` con `a` y `b` ambos `Integer`s crea un `UnitRange`.

# Ejemplos

```jldoctest
julia> collect(UnitRange(2.3, 5.2))
3-element Vector{Float64}:
 2.3
 3.3
 4.3

julia> typeof(1:10)
UnitRange{Int64}
```
