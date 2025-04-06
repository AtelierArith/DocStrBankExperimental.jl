```
rmprocs(pids...; waitfor=typemax(Int))
```

Entfernen Sie die angegebenen Arbeiter. Beachten Sie, dass nur Prozess 1 Arbeiter hinzufügen oder entfernen kann.

Das Argument `waitfor` gibt an, wie lange gewartet werden soll, bis die Arbeiter heruntergefahren sind:

  * Wenn nicht angegeben, wartet `rmprocs`, bis alle angeforderten `pids` entfernt sind.
  * Eine [`ErrorException`](@ref) wird ausgelöst, wenn nicht alle Arbeiter vor den angeforderten `waitfor` Sekunden beendet werden können.
  * Mit einem `waitfor`-Wert von 0 gibt der Aufruf sofort zurück, wobei die Arbeiter in einer anderen Aufgabe zur Entfernung geplant sind. Das geplante [`Task`](@ref) Objekt wird zurückgegeben. Der Benutzer sollte [`wait`](@ref) auf der Aufgabe aufrufen, bevor er andere parallele Aufrufe tätigt.

# Beispiele

```julia-repl
$ julia -p 5

julia> t = rmprocs(2, 3, waitfor=0)
Task (runnable) @0x0000000107c718d0

julia> wait(t)

julia> workers()
3-element Array{Int64,1}:
 4
 5
 6
```
