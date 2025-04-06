```
parse(x::Union{AbstractString, IO})
parse(p::Parser, x::Union{AbstractString, IO})
```

Analyse la chaîne ou le flux `x`, et retourne la table résultante (dictionnaire). Lève une [`ParserError`](@ref) en cas d'échec.

Voir aussi [`TOML.tryparse`](@ref).
