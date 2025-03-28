```
digest!(context)
```

Finalisieren Sie den SHA-Kontext und geben Sie den Hash als Array von Bytes (Array{Uint8, 1}) zurück. Das Aktualisieren des Kontexts nach dem Aufruf von `digest!` darauf wird einen Fehler verursachen.

# Beispiele

```julia-repl
julia> ctx = SHA1_CTX()
SHA1-Hash-Zustand

julia> update!(ctx, b"daten, die gehasht werden sollen")

julia> digest!(ctx)
20-element Array{UInt8,1}:
 0x83
 0xe4
 ⋮
 0x89
 0xf5

julia> update!(ctx, b"weitere Daten")
ERROR: Kann CTX nicht aktualisieren, nachdem `digest!` darauf aufgerufen wurde
[...]
```
