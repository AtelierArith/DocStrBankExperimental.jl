```
oftype(x, y)
```

Konvertiere `y` in den Typ von `x`, d.h. `convert(typeof(x), y)`.

# Beispiele

```jldoctest
julia> x = 4;

julia> y = 3.;

julia> oftype(x, y)
3

julia> oftype(y, x)
4.0
```
