```
bitstring(n)
```

Bir ilkel türün literal bit temsilini veren bir dize.

Ayrıca bkz. [`count_ones`](@ref), [`count_zeros`](@ref), [`digits`](@ref).

# Örnekler

```jldoctest
julia> bitstring(Int32(4))
"00000000000000000000000000000100"

julia> bitstring(2.2)
"0100000000000001100110011001100110011001100110011001100110011010"
```
