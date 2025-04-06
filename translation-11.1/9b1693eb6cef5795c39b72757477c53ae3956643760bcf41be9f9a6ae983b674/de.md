```
mktemp(parent=tempdir(); cleanup=true) -> (path, io)
```

Gibt `(path, io)` zurück, wobei `path` der Pfad einer neuen temporären Datei in `parent` ist und `io` ein offenes Dateiobjekt für diesen Pfad ist. Die Option `cleanup` steuert, ob die temporäre Datei automatisch gelöscht wird, wenn der Prozess beendet wird.

!!! compat "Julia 1.3"
    Das Schlüsselwortargument `cleanup` wurde in Julia 1.3 hinzugefügt. In diesem Zusammenhang wird Julia ab Version 1.3 die temporären Pfade, die von `mktemp` erstellt wurden, entfernen, wenn der Julia-Prozess beendet wird, es sei denn, `cleanup` wird ausdrücklich auf `false` gesetzt.

