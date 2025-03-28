```
widemul(x, y)
```

Multiplica `x` e `y`, dando el resultado como un tipo más grande.

Véase también [`promote`](@ref), [`Base.add_sum`](@ref).

# Ejemplos

```jldoctest
julia> widemul(Float32(3.0), 4.0) isa BigFloat
true

julia> typemax(Int8) * typemax(Int8)
1

julia> widemul(typemax(Int8), typemax(Int8))  # == 127^2
16129
```
