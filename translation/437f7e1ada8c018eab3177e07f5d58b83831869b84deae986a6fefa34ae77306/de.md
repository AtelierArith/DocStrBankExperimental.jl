```
parsefile(f::AbstractString)
parsefile(p::Parser, f::AbstractString)
```

Analysiere die Datei `f` und gib die resultierende Tabelle (Wörterbuch) zurück. Wirf einen [`ParserError`](@ref) im Falle eines Fehlers.

Siehe auch [`TOML.tryparsefile`](@ref).
