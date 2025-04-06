```
dirname(path::AbstractString) -> String
```

Bir yolun dizin kısmını alır. Yoldaki son karakterler ('/' veya '\') yolun bir parçası olarak sayılır.

# Örnekler

```jldoctest
julia> dirname("/home/myuser")
"/home"

julia> dirname("/home/myuser/")
"/home/myuser"
```

Ayrıca [`basename`](@ref) bakınız.
