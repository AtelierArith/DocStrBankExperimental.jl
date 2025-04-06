```
fld1(x, y)
```

División entera, devolviendo un valor consistente con `mod1(x,y)`

Véase también [`mod1`](@ref), [`fldmod1`](@ref).

# Ejemplos

```jldoctest
julia> x = 15; y = 4;

julia> fld1(x, y)
4

julia> x == fld(x, y) * y + mod(x, y)
true

julia> x == (fld1(x, y) - 1) * y + mod1(x, y)
true
```
