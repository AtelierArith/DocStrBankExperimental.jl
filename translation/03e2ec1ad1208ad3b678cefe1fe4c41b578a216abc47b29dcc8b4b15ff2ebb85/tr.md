```
!==(x, y)
≢(x,y)
```

Her zaman [`===`](@ref) ile ters cevap verir.

# Örnekler

```jldoctest
julia> a = [1, 2]; b = [1, 2];

julia> a ≢ b
true

julia> a ≢ a
false
```
