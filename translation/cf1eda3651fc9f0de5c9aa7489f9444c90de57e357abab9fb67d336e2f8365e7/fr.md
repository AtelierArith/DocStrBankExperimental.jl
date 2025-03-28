```
tryparse(x::Union{AbstractString, IO})
tryparse(p::Parser, x::Union{AbstractString, IO})
```

Analyse la chaîne ou le flux `x`, et retourne la table résultante (dictionnaire). Retourne une [`ParserError`](@ref) en cas d'échec.

Voir aussi [`TOML.parse`](@ref).
