```
tryparsefile(f::AbstractString)
tryparsefile(p::Parser, f::AbstractString)
```

Analyse le fichier `f` et retourne la table résultante (dictionnaire). Retourne une [`ParserError`](@ref) en cas d'échec.

Voir aussi [`TOML.parsefile`](@ref).
