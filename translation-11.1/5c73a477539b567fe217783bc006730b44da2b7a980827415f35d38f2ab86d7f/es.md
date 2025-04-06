```
oftype(x, y)
```

Convierte `y` al tipo de `x`, es decir, `convert(typeof(x), y)`.

# Ejemplos

```jldoctest
julia> x = 4;

julia> y = 3.;

julia> oftype(x, y)
3

julia> oftype(y, x)
4.0
```
