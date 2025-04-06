```
iswritable(io) -> Bool
```

Belirtilen IO nesnesi yazılabilir değilse `false` döner.

# Örnekler

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
