```
AbstractWorkerPool
```

Supertyp für Arbeiterpools wie [`WorkerPool`](@ref) und [`CachingPool`](@ref). Ein `AbstractWorkerPool` sollte implementieren:

  * [`push!`](@ref) - einen neuen Arbeiter zum gesamten Pool hinzufügen (verfügbar + beschäftigt)
  * [`put!`](@ref) - einen Arbeiter zurück in den verfügbaren Pool geben
  * [`take!`](@ref) - einen Arbeiter aus dem verfügbaren Pool nehmen (um ihn für die Ausführung von Remote-Funktionen zu verwenden)
  * [`length`](@ref) - Anzahl der im gesamten Pool verfügbaren Arbeiter
  * [`isready`](@ref) - false zurückgeben, wenn ein `take!` auf dem Pool blockieren würde, sonst true

Die Standardimplementierungen der oben genannten Methoden (auf einem `AbstractWorkerPool`) erfordern die Felder

  * `channel::Channel{Int}`
  * `workers::Set{Int}`

wobei `channel` die freien Arbeiter-pids enthält und `workers` die Menge aller Arbeiter ist, die mit diesem Pool verbunden sind.
