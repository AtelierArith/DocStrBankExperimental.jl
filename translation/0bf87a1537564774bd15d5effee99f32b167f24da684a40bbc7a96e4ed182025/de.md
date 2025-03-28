```
localindices(S::SharedArray)
```

Gibt einen Bereich zurück, der die "Standard"-Indizes beschreibt, die vom aktuellen Prozess verarbeitet werden sollen. Dieser Bereich sollte im Sinne der linearen Indizierung interpretiert werden, d.h. als ein Teilbereich von `1:length(S)`. In Mehrprozesskontexten gibt er einen leeren Bereich im übergeordneten Prozess (oder in jedem Prozess, für den [`indexpids`](@ref) 0 zurückgibt) zurück.

Es ist wichtig zu betonen, dass `localindices` rein aus Bequemlichkeit existiert und Sie die Arbeit im Array unter den Arbeitern nach Belieben aufteilen können. Für ein `SharedArray` sollten alle Indizes für jeden Arbeitsprozess gleich schnell sein.
