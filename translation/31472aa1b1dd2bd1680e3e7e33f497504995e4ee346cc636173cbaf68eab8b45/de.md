```
x || y
```

Kurzschluss-Boolean-ODER.

Siehe auch: [`|`](@ref), [`xor`](@ref), [`&&`](@ref).

# Beispiele

```jldoctest
julia> pi < 3 || ℯ < 3
true

julia> false || true || println("keines ist wahr!")
true
```
