```
!==(x, y)
≢(x,y)
```

Siempre da la respuesta opuesta a [`===`](@ref).

# Ejemplos

```jldoctest
julia> a = [1, 2]; b = [1, 2];

julia> a ≢ b
true

julia> a ≢ a
false
```
