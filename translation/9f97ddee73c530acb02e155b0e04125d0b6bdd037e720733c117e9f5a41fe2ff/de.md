```
trylock(lock) -> Erfolg (Boolean)
```

Erwirbt das Schloss, wenn es verfügbar ist, und gibt `true` zurück, wenn es erfolgreich war. Wenn das Schloss bereits von einer anderen Aufgabe/Thread gesperrt ist, gibt es `false` zurück.

Jedes erfolgreiche `trylock` muss mit einem [`unlock`](@ref) übereinstimmen.

Die Funktion `trylock` in Kombination mit [`islocked`](@ref) kann verwendet werden, um die Test-und-Test-und-Set- oder exponentielle Backoff-Algorithmen zu schreiben *wenn es von `typeof(lock)` unterstützt wird* (lesen Sie die Dokumentation dazu).
