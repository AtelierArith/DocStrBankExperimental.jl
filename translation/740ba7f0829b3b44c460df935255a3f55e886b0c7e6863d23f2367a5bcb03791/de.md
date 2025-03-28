```
@elapsed
```

Ein Makro zur Auswertung eines Ausdrucks, wobei der resultierende Wert verworfen wird, stattdessen wird die Anzahl der Sekunden zurückgegeben, die zur Ausführung benötigt wurden, als Fließkommazahl.

In einigen Fällen wird das System innerhalb des `@elapsed`-Ausdrucks nachsehen und einen Teil des aufgerufenen Codes vor der Ausführung des obersten Ausdrucks kompilieren. Wenn das passiert, wird einige Kompilierungszeit nicht gezählt. Um diese Zeit einzuschließen, können Sie `@elapsed @eval ...` ausführen.

Siehe auch [`@time`](@ref), [`@timev`](@ref), [`@timed`](@ref), [`@allocated`](@ref) und [`@allocations`](@ref).

```julia-repl
julia> @elapsed sleep(0.3)
0.301391426
```
