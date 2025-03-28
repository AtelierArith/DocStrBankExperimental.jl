```
take!(b::IOBuffer)
```

Obtiene el contenido de un `IOBuffer` como un arreglo. Después, el `IOBuffer` se restablece a su estado inicial.

# Ejemplos

```jldoctest
julia> io = IOBuffer();

julia> write(io, "JuliaLang is a GitHub organization.", " It has many members.")
56

julia> String(take!(io))
"JuliaLang is a GitHub organization. It has many members."
```
