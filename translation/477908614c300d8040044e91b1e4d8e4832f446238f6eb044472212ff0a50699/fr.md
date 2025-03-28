```
isreadable(io) -> Bool
```

Retourne `false` si l'objet IO spécifié n'est pas lisible.

# Exemples

```jldoctest
julia> open("myfile.txt", "w") do io
           print(io, "Hello world!");
           isreadable(io)
       end
false

julia> open("myfile.txt", "r") do io
           isreadable(io)
       end
true

julia> rm("myfile.txt")
```
