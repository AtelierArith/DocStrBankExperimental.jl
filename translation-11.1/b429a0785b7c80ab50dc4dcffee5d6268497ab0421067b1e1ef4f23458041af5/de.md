```
CompositeException
```

Wickeln Sie einen `Vector` von Ausnahmen, die von einer [`Task`](@ref) ausgelöst wurden (z. B. generiert von einem Remote-Arbeiter über einen Kanal oder einem asynchron ausgeführten lokalen I/O-Schreibvorgang oder einem Remote-Arbeiter unter `pmap`), mit Informationen über die Reihe von Ausnahmen. Wenn beispielsweise eine Gruppe von Arbeitern mehrere Aufgaben ausführt und mehrere Arbeiter fehlschlagen, enthält die resultierende `CompositeException` ein "Bündel" von Informationen von jedem Arbeiter, das angibt, wo und warum die Ausnahme(n) aufgetreten sind.
