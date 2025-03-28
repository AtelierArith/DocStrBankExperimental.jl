```
splitdir(path::AbstractString) -> (AbstractString, AbstractString)
```

Divide una ruta en una tupla del nombre del directorio y el nombre del archivo.

# Ejemplos

```jldoctest
julia> splitdir("/home/myuser")
("/home", "myuser")
```
