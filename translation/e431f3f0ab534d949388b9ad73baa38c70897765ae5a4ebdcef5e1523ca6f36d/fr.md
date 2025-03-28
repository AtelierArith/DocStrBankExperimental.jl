```
iswritable(io) -> Bool
```

Retourne `false` si l'objet IO spécifié n'est pas écrivable.

# Exemples

```jldoctest
julia> open("myfile.txt", "w") do io
           print(io, "Hello world!");
           iswritable(io)
       end
true

julia> open("myfile.txt", "r") do io
           iswritable(io)
       end
false

julia> rm("myfile.txt")
```
