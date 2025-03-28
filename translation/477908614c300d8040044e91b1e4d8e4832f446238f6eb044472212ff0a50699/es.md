```
isreadable(io) -> Bool
```

Devuelve `false` si el objeto IO especificado no es legible.

# Ejemplos

```jldoctest
julia> open("myfile.txt", "w") do io
           print(io, "¡Hola mundo!");
           isreadable(io)
       end
false

julia> open("myfile.txt", "r") do io
           isreadable(io)
       end
true

julia> rm("myfile.txt")
```
