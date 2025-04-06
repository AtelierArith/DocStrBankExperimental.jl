```
!(x)
```

Boolesches Nicht. Implementiert [dreiwertige Logik](https://en.wikipedia.org/wiki/Three-valued_logic), gibt [`missing`](@ref) zurück, wenn `x` `missing` ist.

Siehe auch [`~`](@ref) für bitweises Nicht.

# Beispiele

```jldoctest
julia> !true
false

julia> !false
true

julia> !missing
missing

julia> .![true false true]
1×3 BitMatrix:
 0  1  0
```
