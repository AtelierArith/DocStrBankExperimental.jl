```
isreadable(io) -> Bool
```

Belirtilen IO nesnesi okunabilir değilse `false` döndürür.

# Örnekler

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
