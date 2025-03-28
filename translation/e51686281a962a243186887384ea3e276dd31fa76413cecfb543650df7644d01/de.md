```
isa(x, type) -> Bool
```

Bestimmen Sie, ob `x` vom angegebenen `type` ist. Kann auch als infix Operator verwendet werden, z.B. `x isa type`.

# Beispiele

```jldoctest
julia> isa(1, Int)
true

julia> isa(1, Matrix)
false

julia> isa(1, Char)
false

julia> isa(1, Number)
true

julia> 1 isa Number
true
```
