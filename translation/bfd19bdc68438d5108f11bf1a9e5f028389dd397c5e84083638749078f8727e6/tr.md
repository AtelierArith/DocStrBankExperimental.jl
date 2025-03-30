```
widemul(x, y)
```

`x` ve `y`'yi çarpar, sonucu daha büyük bir türde verir.

Ayrıca bkz. [`promote`](@ref), [`Base.add_sum`](@ref).

# Örnekler

```jldoctest
julia> widemul(Float32(3.0), 4.0) isa BigFloat
true

julia> typemax(Int8) * typemax(Int8)
1

julia> widemul(typemax(Int8), typemax(Int8))  # == 127^2
16129
```
