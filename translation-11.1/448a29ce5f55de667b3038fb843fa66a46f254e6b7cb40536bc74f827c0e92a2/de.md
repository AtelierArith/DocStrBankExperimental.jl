```
parse(x::Union{AbstractString, IO})
parse(p::Parser, x::Union{AbstractString, IO})
```

Analysiere den String oder Stream `x` und gib die resultierende Tabelle (Wörterbuch) zurück. Wirf einen [`ParserError`](@ref) im Falle eines Fehlers.

Siehe auch [`TOML.tryparse`](@ref).
