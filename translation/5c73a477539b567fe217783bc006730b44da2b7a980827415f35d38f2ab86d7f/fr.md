```
oftype(x, y)
```

Convertir `y` au type de `x`, c'est-à-dire `convert(typeof(x), y)`.

# Exemples

```jldoctest
julia> x = 4;

julia> y = 3.;

julia> oftype(x, y)
3

julia> oftype(y, x)
4.0
```
