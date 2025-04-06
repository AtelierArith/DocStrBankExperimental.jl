```
systemsleep(s::Real)
```

Unterbricht die Ausführung für `s` Sekunden. Diese Funktion gibt nicht an den Julia-Scheduler ab und blockiert daher den Julia-Thread, auf dem sie ausgeführt wird, für die Dauer der Schlafzeit.

Siehe auch [`sleep`](@ref).
