```
tryparsefile(f::AbstractString)
tryparsefile(p::Parser, f::AbstractString)
```

Analiza el archivo `f` y devuelve la tabla resultante (diccionario). Devuelve un [`ParserError`](@ref) en caso de fallo.

Ver también [`TOML.parsefile`](@ref).
