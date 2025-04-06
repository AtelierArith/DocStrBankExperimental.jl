```
isdigit(c::AbstractChar) -> Bool
```

Überprüft, ob ein Zeichen eine Dezimalziffer (0-9) ist.

Siehe auch: [`isletter`](@ref).

# Beispiele

```jldoctest
julia> isdigit('❤')
false

julia> isdigit('9')
true

julia> isdigit('α')
false
```
