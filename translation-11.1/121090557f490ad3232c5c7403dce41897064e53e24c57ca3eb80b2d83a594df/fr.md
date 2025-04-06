```
bitrotate(x::Base.BitInteger, k::Integer)
```

`bitrotate(x, k)` implémente la rotation binaire. Il renvoie la valeur de `x` avec ses bits tournés à gauche `k` fois. Une valeur négative de `k` tournera à droite à la place.

!!! compat "Julia 1.5"
    Cette fonction nécessite Julia 1.5 ou une version ultérieure.


Voir aussi : [`<<`](@ref), [`circshift`](@ref), [`BitArray`](@ref).

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
