```
remote([p::AbstractWorkerPool], f) -> Funktion
```

Gibt eine anonyme Funktion zurück, die die Funktion `f` auf einem verfügbaren Arbeiter (aus dem [`WorkerPool`](@ref) `p`, falls angegeben) unter Verwendung von [`remotecall_fetch`](@ref) ausführt.
