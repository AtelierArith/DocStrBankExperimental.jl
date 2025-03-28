```
string(n::Integer; base::Integer = 10, pad::Integer = 1)
```

Konvertiert eine Ganzzahl `n` in einen String in der angegebenen `Basis`, wobei optional eine Anzahl von Ziffern zum Auffüllen angegeben werden kann.

Siehe auch [`digits`](@ref), [`bitstring`](@ref), [`count_zeros`](@ref).

# Beispiele

```jldoctest
julia> string(5, base = 13, pad = 4)
"0005"

julia> string(-13, base = 5, pad = 4)
"-0023"
```
