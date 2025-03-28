```
floatmax(T = Float64)
```

Devuelve el número finito más grande que se puede representar con el tipo de punto flotante `T`.

Véase también: [`typemax`](@ref), [`floatmin`](@ref), [`eps`](@ref).

# Ejemplos

```jldoctest
julia> floatmax(Float16)
Float16(6.55e4)

julia> floatmax(Float32)
3.4028235f38

julia> floatmax()
1.7976931348623157e308

julia> typemax(Float64)
Inf
```
