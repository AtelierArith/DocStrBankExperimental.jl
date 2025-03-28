```
mktempdir(parent=tempdir(); prefix="jl_", cleanup=true) -> path
```

Erstellt ein temporäres Verzeichnis im `parent`-Verzeichnis mit einem Namen, der aus dem angegebenen `prefix` und einem zufälligen Suffix zusammengesetzt ist, und gibt dessen Pfad zurück. Darüber hinaus können auf einigen Plattformen alle nachfolgenden `'X'`-Zeichen im `prefix` durch zufällige Zeichen ersetzt werden. Wenn `parent` nicht existiert, wird ein Fehler ausgelöst. Die `cleanup`-Option steuert, ob das temporäre Verzeichnis automatisch gelöscht wird, wenn der Prozess beendet wird.

!!! compat "Julia 1.2"
    Das Schlüsselwort-Argument `prefix` wurde in Julia 1.2 hinzugefügt.


!!! compat "Julia 1.3"
    Das Schlüsselwort-Argument `cleanup` wurde in Julia 1.3 hinzugefügt. In diesem Zusammenhang wird Julia ab Version 1.3 die temporären Pfade, die von `mktempdir` erstellt wurden, entfernen, wenn der Julia-Prozess beendet wird, es sei denn, `cleanup` wird ausdrücklich auf `false` gesetzt.


Siehe auch: [`mktemp`](@ref), [`mkdir`](@ref).
