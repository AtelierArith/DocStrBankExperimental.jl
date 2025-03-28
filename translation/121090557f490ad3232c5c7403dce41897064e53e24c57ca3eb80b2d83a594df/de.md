```
bitrotate(x::Base.BitInteger, k::Integer)
```

`bitrotate(x, k)` implementiert eine bitweise Rotation. Es gibt den Wert von `x` zurück, dessen Bits `k` Mal nach links rotiert wurden. Ein negativer Wert von `k` rotiert stattdessen nach rechts.

!!! compat "Julia 1.5"
    Diese Funktion erfordert Julia 1.5 oder höher.


Siehe auch: [`<<`](@ref), [`circshift`](@ref), [`BitArray`](@ref).

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
