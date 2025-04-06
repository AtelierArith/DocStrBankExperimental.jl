```
isdirpath(path::AbstractString) -> Bool
```

Bir yolun bir dizini ifade edip etmediğini belirleyin (örneğin, bir yol ayırıcı ile bitiyorsa).

# Örnekler

```jldoctest
julia> isdirpath("/home")
false

julia> isdirpath("/home/")
true
```
