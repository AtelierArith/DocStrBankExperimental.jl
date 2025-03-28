```
bitstring(n)
```

Una cadena que da la representación literal en bits de un tipo primitivo.

Véase también [`count_ones`](@ref), [`count_zeros`](@ref), [`digits`](@ref).

# Ejemplos

```jldoctest
julia> bitstring(Int32(4))
"00000000000000000000000000000100"

julia> bitstring(2.2)
"0100000000000001100110011001100110011001100110011001100110011010"
```
