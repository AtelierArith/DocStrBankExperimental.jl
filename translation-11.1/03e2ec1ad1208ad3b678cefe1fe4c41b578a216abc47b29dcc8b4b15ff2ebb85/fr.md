```
!==(x, y)
≢(x,y)
```

Donne toujours la réponse opposée à [`===`](@ref).

# Exemples

```jldoctest
julia> a = [1, 2]; b = [1, 2];

julia> a ≢ b
true

julia> a ≢ a
false
```
