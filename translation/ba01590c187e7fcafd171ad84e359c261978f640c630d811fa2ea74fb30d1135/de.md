```
fld1(x, y)
```

Bodendivision, die einen Wert zurückgibt, der mit `mod1(x,y)` übereinstimmt.

Siehe auch [`mod1`](@ref), [`fldmod1`](@ref).

# Beispiele

```jldoctest
julia> x = 15; y = 4;

julia> fld1(x, y)
4

julia> x == fld(x, y) * y + mod(x, y)
true

julia> x == (fld1(x, y) - 1) * y + mod1(x, y)
true
```
