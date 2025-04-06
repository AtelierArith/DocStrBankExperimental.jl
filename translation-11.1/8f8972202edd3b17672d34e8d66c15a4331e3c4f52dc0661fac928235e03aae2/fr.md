```
bitstring(n)
```

Une chaîne donnant la représentation binaire littérale d'un type primitif.

Voir aussi [`count_ones`](@ref), [`count_zeros`](@ref), [`digits`](@ref).

# Exemples

```jldoctest
julia> bitstring(Int32(4))
"00000000000000000000000000000100"

julia> bitstring(2.2)
"0100000000000001100110011001100110011001100110011001100110011010"
```
