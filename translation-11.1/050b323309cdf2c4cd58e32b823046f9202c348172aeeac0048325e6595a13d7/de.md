```
find_artifacts_toml(pfad::String)
```

Gegeben den Pfad zu einer `.jl`-Datei (wie der, die von `__source__.file` im Kontext eines Makros zurückgegeben wird), finde die `(Julia)Artifacts.toml`, die im übergeordneten Projekt enthalten ist (sofern vorhanden), andernfalls gib `nichts` zurück.

!!! kompatibel "Julia 1.3"
    Diese Funktion erfordert mindestens Julia 1.3.

