```
mktemp(f::Function, parent=tempdir())
```

Wenden Sie die Funktion `f` auf das Ergebnis von [`mktemp(parent)`](@ref) an und entfernen Sie die temporäre Datei nach Abschluss.

Siehe auch: [`mktempdir`](@ref).
