```
oftype(x, y)
```

`y`'yi `x`'in türüne dönüştürür, yani `convert(typeof(x), y)`.

# Örnekler

```jldoctest
julia> x = 4;

julia> y = 3.;

julia> oftype(x, y)
3

julia> oftype(y, x)
4.0
```
