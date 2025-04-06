```
Sys.username() -> String
```

Gibt den Benutzernamen des aktuellen Benutzers zurück. Wenn der Benutzername nicht bestimmt werden kann oder leer ist, wirft diese Funktion einen Fehler.

Um einen Benutzernamen abzurufen, der über eine Umgebungsvariable überschreibbar ist, z. B. `USER`, sollten Sie Folgendes verwenden:

```julia
user = get(Sys.username, ENV, "USER")
```

!!! compat "Julia 1.11"
    Diese Funktion erfordert mindestens Julia 1.11.


Siehe auch [`homedir`](@ref).
