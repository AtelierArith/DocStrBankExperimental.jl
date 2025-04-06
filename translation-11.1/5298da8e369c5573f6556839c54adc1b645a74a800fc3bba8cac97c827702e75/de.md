```
open(f::Function, command, args...; kwargs...)
```

Ähnlich wie `open(command, args...; kwargs...)`, aber ruft `f(stream)` auf dem resultierenden Prozessstream auf, schließt dann den Eingabestream und wartet, bis der Prozess abgeschlossen ist. Gibt den Wert zurück, den `f` bei Erfolg zurückgibt. Wirft einen Fehler, wenn der Prozess fehlgeschlagen ist oder wenn der Prozess versucht, etwas auf stdout auszugeben.
