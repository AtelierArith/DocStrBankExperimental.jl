```
iswritable(io) -> Bool
```

Gibt `false` zurück, wenn das angegebene IO-Objekt nicht beschreibbar ist.

# Beispiele

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
