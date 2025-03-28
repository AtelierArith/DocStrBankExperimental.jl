```
tryparsefile(f::AbstractString)
tryparsefile(p::Parser, f::AbstractString)
```

Analysiere die Datei `f` und gib die resultierende Tabelle (Wörterbuch) zurück. Gib einen [`ParserError`](@ref) im Falle eines Fehlers zurück.

Siehe auch [`TOML.parsefile`](@ref).
