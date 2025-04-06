```
pathof(m::Module)
```

Gibt den Pfad der `m.jl`-Datei zurück, die verwendet wurde, um das Modul `m` zu `importieren`, oder `nothing`, wenn `m` nicht aus einem Paket importiert wurde.

Verwenden Sie [`dirname`](@ref), um den Verzeichnisteil und [`basename`](@ref), um den Dateinamen des Pfads zu erhalten.

Siehe auch [`pkgdir`](@ref).
