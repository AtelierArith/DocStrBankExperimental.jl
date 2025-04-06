```
@doc_str -> MD
```

Analiza la cadena dada como texto Markdown, agrega información de línea y módulo y devuelve un objeto correspondiente [`MD`](@ref).

`@doc_str` se puede usar en conjunto con el módulo [`Base.Docs`](@ref). También consulte la sección del manual sobre [documentación](@ref man-documentation) para obtener más información.

# Ejemplos

```
julia> s = doc"f(x) = 2*x"
  f(x) = 2*x

julia> typeof(s)
Markdown.MD

```
