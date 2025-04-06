```
bitrotate(x::Base.BitInteger, k::Integer)
```

`bitrotate(x, k)` bit düzeyinde döndürme işlemi gerçekleştirir. `x`'in bitlerini `k` kez sola döndürerek değerini döndürür. `k`'nın negatif bir değeri sağa döndürme işlemi yapar.

!!! compat "Julia 1.5"
    Bu fonksiyon Julia 1.5 veya daha yenisini gerektirir.


Ayrıca bakınız: [`<<`](@ref), [`circshift`](@ref), [`BitArray`](@ref).

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
