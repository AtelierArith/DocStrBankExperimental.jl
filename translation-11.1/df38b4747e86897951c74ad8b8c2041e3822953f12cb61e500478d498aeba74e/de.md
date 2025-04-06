```
x & y
```

Bitweises und. Implementiert [dreiwertige Logik](https://de.wikipedia.org/wiki/Dreiwertige_Logik), gibt [`missing`](@ref) zurück, wenn ein Operand `missing` ist und der andere `true`. Fügen Sie Klammern für die Funktionsanwendungsform hinzu: `(&)(x, y)`.

Siehe auch: [`|`](@ref), [`xor`](@ref), [`&&`](@ref).

# Beispiele

```jldoctest
julia> 4 & 10
0

julia> 4 & 12
4

julia> true & missing
missing

julia> false & missing
false
```
