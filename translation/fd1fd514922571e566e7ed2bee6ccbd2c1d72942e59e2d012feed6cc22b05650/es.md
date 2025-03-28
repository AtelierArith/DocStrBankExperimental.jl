```
typemax(T)
```

El valor más alto que se puede representar con el `DataType` numérico (real) dado.

Véase también: [`floatmax`](@ref), [`typemin`](@ref), [`eps`](@ref).

# Ejemplos

```jldoctest
julia> typemax(Int8)
127

julia> typemax(UInt32)
0xffffffff

julia> typemax(Float64)
Inf

julia> typemax(Float32)
Inf32

julia> floatmax(Float32)  # el número de punto flotante Finito más grande de Float32
3.4028235f38
```
