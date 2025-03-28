```
realloc(addr::Ptr, size::Integer) -> Ptr{Cvoid}
```

Ruft `realloc` aus der C-Standardbibliothek auf.

Siehe Warnung in der Dokumentation für [`free`](@ref) bezüglich der Verwendung nur für Speicher, der ursprünglich von [`malloc`](@ref) erhalten wurde.
