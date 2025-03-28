```
eachmatch(r::Regex, s::AbstractString; overlap::Bool=false)
```

Busca todas las coincidencias de la expresión regular `r` en `s` y devuelve un iterador sobre las coincidencias. Si `overlap` es `true`, las secuencias coincidentes pueden superponerse en los índices de la cadena original, de lo contrario, deben ser de rangos de caracteres distintos.

# Ejemplos

```jldoctest
julia> rx = r"a.a"
r"a.a"

julia> m = eachmatch(rx, "a1a2a3a")
Base.RegexMatchIterator{String}(r"a.a", "a1a2a3a", false)

julia> collect(m)
2-element Vector{RegexMatch}:
 RegexMatch("a1a")
 RegexMatch("a3a")

julia> collect(eachmatch(rx, "a1a2a3a", overlap = true))
3-element Vector{RegexMatch}:
 RegexMatch("a1a")
 RegexMatch("a2a")
 RegexMatch("a3a")
```
