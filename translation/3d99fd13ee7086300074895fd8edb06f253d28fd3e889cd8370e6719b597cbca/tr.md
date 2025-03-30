```
splitdir(path::AbstractString) -> (AbstractString, AbstractString)
```

Bir yolu dizin adı ve dosya adı içeren bir demet haline ayırır.

# Örnekler

```jldoctest
julia> splitdir("/home/myuser")
("/home", "myuser")
```
