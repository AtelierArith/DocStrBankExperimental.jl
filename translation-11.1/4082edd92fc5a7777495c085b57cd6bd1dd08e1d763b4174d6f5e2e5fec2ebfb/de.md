```
isexecutable(path::String)
```

Gibt `true` zurück, wenn der angegebene `path` ausführbare Berechtigungen hat.

!!! note
    Diese Berechtigung kann sich ändern, bevor der Benutzer `path` ausführt, daher wird empfohlen, die Datei auszuführen und den Fehler zu behandeln, falls dies fehlschlägt, anstatt zuerst `isexecutable` aufzurufen.


!!! note
    Vor Julia 1.6 wurde dies nicht korrekt für die Dateisystem-ACLs unter Windows abgefragt, daher gab es für jede Datei `true` zurück. Ab Julia 1.6 wird korrekt bestimmt, ob die Datei als ausführbar markiert ist oder nicht.


Siehe auch [`ispath`](@ref), [`isreadable`](@ref), [`iswritable`](@ref).
