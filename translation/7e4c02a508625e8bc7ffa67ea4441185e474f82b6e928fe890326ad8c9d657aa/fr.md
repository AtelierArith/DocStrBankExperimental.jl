```
bytesavailable(io)
```

Renvoie le nombre d'octets disponibles pour la lecture avant qu'une lecture de ce flux ou tampon ne bloque.

# Exemples

```jldoctest
julia> io = IOBuffer("JuliaLang est une organisation GitHub");

julia> bytesavailable(io)
34
```
