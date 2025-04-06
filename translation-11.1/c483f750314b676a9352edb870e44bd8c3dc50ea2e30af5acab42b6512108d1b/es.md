```
typemin(T)
```

El valor más bajo que se puede representar con el tipo de dato numérico (real) dado `T`.

Véase también: [`floatmin`](@ref), [`typemax`](@ref), [`eps`](@ref).

# Ejemplos

```jldoctest
julia> typemin(Int8)
-128

julia> typemin(UInt32)
0x00000000

julia> typemin(Float16)
-Inf16

julia> typemin(Float32)
-Inf32

julia> nextfloat(-Inf32)  # el número de punto flotante Float32 finito más pequeño
-3.4028235f38
```
