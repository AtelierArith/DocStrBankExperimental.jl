```
update!(context, data[, datalen])
```

Aktualisieren Sie den SHA-Kontext mit den Bytes in data. Siehe auch [`digest!`](@ref) zum Finalisieren des Hashs.

# Beispiele

```julia-repl
julia> ctx = SHA1_CTX()
SHA1-Hash-Zustand

julia> update!(ctx, b"daten, die gehasht werden sollen")
```
