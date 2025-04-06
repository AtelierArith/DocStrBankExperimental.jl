```
x | y
```

Bitweises Oder. Implementiert [dreiwertige Logik](https://en.wikipedia.org/wiki/Three-valued_logic), gibt [`missing`](@ref) zurück, wenn ein Operand `missing` und der andere `false` ist.

Siehe auch: [`&`](@ref), [`xor`](@ref), [`||`](@ref).

# Beispiele

```jldoctest
julia> 4 | 10
14

julia> 4 | 1
5

julia> true | missing
true

julia> false | missing
missing
```
