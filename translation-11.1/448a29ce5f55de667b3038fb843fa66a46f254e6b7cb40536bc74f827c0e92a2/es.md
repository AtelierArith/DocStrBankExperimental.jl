```
parse(x::Union{AbstractString, IO})
parse(p::Parser, x::Union{AbstractString, IO})
```

Analiza la cadena o flujo `x`, y devuelve la tabla resultante (diccionario). Lanza un [`ParserError`](@ref) en caso de fallo.

Ver también [`TOML.tryparse`](@ref).
