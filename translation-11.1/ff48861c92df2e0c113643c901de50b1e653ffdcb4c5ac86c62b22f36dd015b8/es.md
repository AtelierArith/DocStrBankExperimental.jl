```
istextmime(m::MIME)
```

Determina si un tipo MIME es datos de texto. Se asume que los tipos MIME son datos binarios, excepto por un conjunto de tipos que se sabe que son datos de texto (posiblemente Unicode).

# Ejemplos

```jldoctest
julia> istextmime(MIME("text/plain"))
true

julia> istextmime(MIME("image/png"))
false
```
