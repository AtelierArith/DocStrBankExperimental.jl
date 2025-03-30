```
bitrotate(x::Base.BitInteger, k::Integer)
```

`bitrotate(x, k)`는 비트 회전을 구현합니다. 이는 `x`의 비트를 `k`번 왼쪽으로 회전한 값을 반환합니다. `k`의 음수 값은 대신 오른쪽으로 회전합니다.

!!! compat "Julia 1.5"
    이 함수는 Julia 1.5 이상이 필요합니다.


참고: [`<<`](@ref), [`circshift`](@ref), [`BitArray`](@ref).

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
