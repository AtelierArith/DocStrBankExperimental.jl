```
redirect_stdout([stream]) -> stream
```

Erstellt ein Pipe, an das alle C- und Julia-Ebene [`stdout`](@ref) Ausgaben umgeleitet werden. Gibt einen Stream zurück, der die Enden des Pipes darstellt. Daten, die in [`stdout`](@ref) geschrieben werden, können jetzt vom `rd` Ende des Pipes gelesen werden.

!!! Hinweis     `stream` muss ein kompatibles Objekt sein, wie ein `IOStream`, `TTY`, [`Pipe`](@ref), Socket oder `devnull`.

Siehe auch [`redirect_stdio`](@ref).
