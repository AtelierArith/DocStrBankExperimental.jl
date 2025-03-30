```
isabspath(path::AbstractString) -> Bool
```

Bir yolun mutlak olup olmadığını belirleyin (kök dizininden başlar).

# Örnekler

```jldoctest
julia> isabspath("/home")
true

julia> isabspath("home")
false
```
