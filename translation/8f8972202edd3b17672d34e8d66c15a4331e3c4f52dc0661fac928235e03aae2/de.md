```
bitstring(n)
```

Ein String, der die literale Bitdarstellung eines primitiven Typs angibt.

Siehe auch [`count_ones`](@ref), [`count_zeros`](@ref), [`digits`](@ref).

# Beispiele

```jldoctest
julia> bitstring(Int32(4))
"00000000000000000000000000000100"

julia> bitstring(2.2)
"0100000000000001100110011001100110011001100110011001100110011010"
```
