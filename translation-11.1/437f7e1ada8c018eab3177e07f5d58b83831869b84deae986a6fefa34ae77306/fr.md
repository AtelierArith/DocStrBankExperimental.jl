```
parsefile(f::AbstractString)
parsefile(p::Parser, f::AbstractString)
```

Analyse le fichier `f` et retourne la table résultante (dictionnaire). Lève une [`ParserError`](@ref) en cas d'échec.

Voir aussi [`TOML.tryparsefile`](@ref).
