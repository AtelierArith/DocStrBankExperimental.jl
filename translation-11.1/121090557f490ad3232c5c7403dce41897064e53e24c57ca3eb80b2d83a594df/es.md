```
bitrotate(x::Base.BitInteger, k::Integer)
```

`bitrotate(x, k)` implementa la rotación a nivel de bits. Devuelve el valor de `x` con sus bits rotados a la izquierda `k` veces. Un valor negativo de `k` rotará a la derecha en su lugar.

!!! compat "Julia 1.5"
    Esta función requiere Julia 1.5 o posterior.


Véase también: [`<<`](@ref), [`circshift`](@ref), [`BitArray`](@ref).

```jldoctest
julia> bitrotate(UInt8(114), 2)
0xc9

julia> bitstring(bitrotate(0b01110010, 2))
"11001001"

julia> bitstring(bitrotate(0b01110010, -2))
"10011100"

julia> bitstring(bitrotate(0b01110010, 8))
"01110010"
```
