```
iswritable(path::String)
```

Gibt `true` zurück, wenn die Zugriffsberechtigungen für den angegebenen `path` das Schreiben durch den aktuellen Benutzer erlauben.

!!! note
    Diese Berechtigung kann sich ändern, bevor der Benutzer `open` aufruft, daher wird empfohlen, einfach `open` allein aufzurufen und den Fehler zu behandeln, falls dies fehlschlägt, anstatt zuerst `iswritable` aufzurufen.


!!! note
    Derzeit kann diese Funktion die Dateisystem-ACLs unter Windows nicht korrekt abfragen, daher kann sie falsche Ergebnisse zurückgeben.


!!! compat "Julia 1.11"
    Diese Funktion erfordert mindestens Julia 1.11.


Siehe auch [`ispath`](@ref), [`isexecutable`](@ref), [`isreadable`](@ref).
