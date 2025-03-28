```
tryparse(x::Union{AbstractString, IO})
tryparse(p::Parser, x::Union{AbstractString, IO})
```

Analysiere den String oder Stream `x` und gib die resultierende Tabelle (Wörterbuch) zurück. Gib einen [`ParserError`](@ref) im Falle eines Fehlers zurück.

Siehe auch [`TOML.parse`](@ref).
