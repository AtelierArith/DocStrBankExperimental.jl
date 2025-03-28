```
parsefile(f::AbstractString)
parsefile(p::Parser, f::AbstractString)
```

Analiza el archivo `f` y devuelve la tabla resultante (diccionario). Lanza un [`ParserError`](@ref) en caso de fallo.

Véase también [`TOML.tryparsefile`](@ref).
