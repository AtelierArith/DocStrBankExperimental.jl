```
iswritable(io) -> Bool
```

Devuelve `false` si el objeto IO especificado no es escribible.

# Ejemplos

```jldoctest
julia> open("myfile.txt", "w") do io
           print(io, "¡Hola mundo!");
           iswritable(io)
       end
true

julia> open("myfile.txt", "r") do io
           iswritable(io)
       end
false

julia> rm("myfile.txt")
```
