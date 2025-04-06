```
tryparse(x::Union{AbstractString, IO})
tryparse(p::Parser, x::Union{AbstractString, IO})
```

Analiza la cadena o flujo `x`, y devuelve la tabla resultante (diccionario). Devuelve un [`ParserError`](@ref) en caso de fallo.

Ver también [`TOML.parse`](@ref).
