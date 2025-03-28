```
mktempdir(f::Function, parent=tempdir(); prefix="jl_")
```

Wenden Sie die Funktion `f` auf das Ergebnis von [`mktempdir(parent; prefix)`](@ref) an und entfernen Sie das temporäre Verzeichnis sowie dessen gesamten Inhalt nach Abschluss.

Siehe auch: [`mktemp`](@ref), [`mkdir`](@ref).

!!! compat "Julia 1.2"
    Das Schlüsselwortargument `prefix` wurde in Julia 1.2 hinzugefügt.

