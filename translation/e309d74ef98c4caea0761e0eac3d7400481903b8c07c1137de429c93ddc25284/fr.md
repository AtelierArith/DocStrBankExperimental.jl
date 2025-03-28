```
take!(b::IOBuffer)
```

Obtenez le contenu d'un `IOBuffer` sous forme de tableau. Ensuite, le `IOBuffer` est réinitialisé à son état initial.

# Exemples

```jldoctest
julia> io = IOBuffer();

julia> write(io, "JuliaLang est une organisation GitHub.", " Elle a de nombreux membres.")
56

julia> String(take!(io))
"JuliaLang est une organisation GitHub. Elle a de nombreux membres."
```
