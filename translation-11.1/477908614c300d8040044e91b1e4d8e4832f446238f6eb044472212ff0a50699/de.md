```
isreadable(io) -> Bool
```

Gibt `false` zurück, wenn das angegebene IO-Objekt nicht lesbar ist.

# Beispiele

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
