```
islocked(lock) -> Status (Boolean)
```

Überprüfen, ob das `lock` von einer Aufgabe/Thread gehalten wird. Diese Funktion allein sollte nicht zur Synchronisation verwendet werden. Allerdings kann `islocked` in Kombination mit [`trylock`](@ref) verwendet werden, um die Test-and-Test-and-Set- oder Exponential-Backoff-Algorithmen zu schreiben, *wenn dies von `typeof(lock)` unterstützt wird* (lesen Sie die Dokumentation).

# Erweiterte Hilfe

Ein exponentieller Backoff kann beispielsweise wie folgt implementiert werden, wenn die `lock`-Implementierung die unten dokumentierten Eigenschaften erfüllt.

```julia
nspins = 0
while true
    while islocked(lock)
        GC.safepoint()
        nspins += 1
        nspins > LIMIT && error("timeout")
    end
    trylock(lock) && break
    backoff()
end
```

## Implementierung

Es wird empfohlen, dass eine Lock-Implementierung `islocked` mit den folgenden Eigenschaften definiert und in ihrer Dokumentation vermerkt:

  * `islocked(lock)` ist datarace-frei.
  * Wenn `islocked(lock)` `false` zurückgibt, muss ein sofortiger Aufruf von `trylock(lock)` erfolgreich sein (gibt `true` zurück), wenn es keine Störungen durch andere Aufgaben gibt.
