```
fld1(x, y)
```

Division entière, retournant une valeur cohérente avec `mod1(x,y)`

Voir aussi [`mod1`](@ref), [`fldmod1`](@ref).

# Exemples

```jldoctest
julia> x = 15; y = 4;

julia> fld1(x, y)
4

julia> x == fld(x, y) * y + mod(x, y)
true

julia> x == (fld1(x, y) - 1) * y + mod1(x, y)
true
```
