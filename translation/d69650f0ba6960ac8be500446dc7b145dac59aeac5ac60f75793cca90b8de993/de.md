```
read(filename::AbstractString)
```

Lese den gesamten Inhalt einer Datei als `Vector{UInt8}`.

```
read(filename::AbstractString, String)
```

Lese den gesamten Inhalt einer Datei als Zeichenfolge.

```
read(filename::AbstractString, args...)
```

Öffne eine Datei und lese ihren Inhalt. `args` wird an `read` übergeben: dies entspricht `open(io->read(io, args...), filename)`.
