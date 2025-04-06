```
isa(x, type) -> Bool
```

Determina si `x` es del tipo dado `type`. También se puede usar como un operador infijo, por ejemplo, `x isa type`.

# Ejemplos

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
