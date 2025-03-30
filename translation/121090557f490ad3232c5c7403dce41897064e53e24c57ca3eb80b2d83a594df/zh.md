```
bitrotate(x::Base.BitInteger, k::Integer)
```

`bitrotate(x, k)` 实现了按位旋转。它返回 `x` 的值，其位向左旋转 `k` 次。负值的 `k` 将向右旋转。

!!! compat "Julia 1.5"
    此函数需要 Julia 1.5 或更高版本。


另见: [`<<`](@ref), [`circshift`](@ref), [`BitArray`](@ref).

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
