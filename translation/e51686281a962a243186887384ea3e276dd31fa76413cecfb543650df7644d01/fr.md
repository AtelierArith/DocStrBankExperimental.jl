```
isa(x, type) -> Bool
```

Détermine si `x` est du type donné `type`. Peut également être utilisé comme un opérateur infixe, par exemple `x isa type`.

# Exemples

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
