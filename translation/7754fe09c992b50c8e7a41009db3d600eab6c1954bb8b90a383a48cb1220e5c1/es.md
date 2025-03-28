```
@md_str -> MD
```

Analiza la cadena dada como texto Markdown y devuelve un objeto correspondiente [`MD`](@ref).

# Ejemplos

```jldoctest
julia> s = md"# Hola, mundo!"
  Hola, mundo!
  ≡≡≡≡≡≡≡≡≡≡≡≡≡

julia> typeof(s)
Markdown.MD

```
