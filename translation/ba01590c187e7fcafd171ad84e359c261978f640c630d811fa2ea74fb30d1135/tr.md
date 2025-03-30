```
fld1(x, y)
```

Kattığı bölme, `mod1(x,y)` ile tutarlı bir değer döndürür.

Ayrıca bkz. [`mod1`](@ref), [`fldmod1`](@ref).

# Örnekler

```jldoctest
julia> x = 15; y = 4;

julia> fld1(x, y)
4

julia> x == fld(x, y) * y + mod(x, y)
true

julia> x == (fld1(x, y) - 1) * y + mod1(x, y)
true
```
