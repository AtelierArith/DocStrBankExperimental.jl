```
@time expr
@time "beschreibung" expr
```

Ein Makro zur Ausführung eines Ausdrucks, das die Zeit, die zur Ausführung benötigt wurde, die Anzahl der Allokationen und die Gesamtzahl der Bytes, die durch die Ausführung allokiert wurden, ausgibt, bevor der Wert des Ausdrucks zurückgegeben wird. Jegliche Zeit, die mit der Müllsammlung (gc), dem Kompilieren neuer Codes oder dem Re-Kompilieren ungültiger Codes verbracht wurde, wird als Prozentsatz angezeigt. Jegliche Lock-Konflikte, bei denen ein [`ReentrantLock`](@ref) warten musste, werden als Anzahl angezeigt.

Optional kann eine Beschreibung als String angegeben werden, die vor dem Zeitbericht ausgegeben wird.

In einigen Fällen wird das System innerhalb des `@time`-Ausdrucks nachsehen und einen Teil des aufgerufenen Codes vor der Ausführung des obersten Ausdrucks kompilieren. Wenn das passiert, wird einige Kompilierungszeit nicht gezählt. Um diese Zeit einzuschließen, können Sie `@time @eval ...` ausführen.

Siehe auch [`@showtime`](@ref), [`@timev`](@ref), [`@timed`](@ref), [`@elapsed`](@ref), [`@allocated`](@ref) und [`@allocations`](@ref).

!!! Hinweis     Für ernsthafteres Benchmarking ziehen Sie das `@btime`-Makro aus dem BenchmarkTools.jl-Paket in Betracht, das unter anderem die Funktion mehrfach auswertet, um Rauschen zu reduzieren.

!!! Kompatibilität "Julia 1.8"     Die Option, eine Beschreibung hinzuzufügen, wurde in Julia 1.8 eingeführt.

```
Die separate Anzeige der Re-Kompilierungszeit von der Kompilierungszeit wurde in Julia 1.8 eingeführt.
```

!!! Kompatibilität "Julia 1.11"     Die Berichterstattung über Lock-Konflikte wurde in Julia 1.11 hinzugefügt.

```julia-repl
julia> x = rand(10,10);

julia> @time x * x;
  0.606588 Sekunden (2.19 M Allokationen: 116.555 MiB, 3.75% gc Zeit, 99.94% Kompilierungszeit)

julia> @time x * x;
  0.000009 Sekunden (1 Allokation: 896 Bytes)

julia> @time begin
           sleep(0.3)
           1+1
       end
  0.301395 Sekunden (8 Allokationen: 336 Bytes)
2

julia> @time "Ein einsekündiger Schlaf" sleep(1)
Ein einsekündiger Schlaf: 1.005750 Sekunden (5 Allokationen: 144 Bytes)

julia> for loop in 1:3
            @time loop sleep(1)
        end
1: 1.006760 Sekunden (5 Allokationen: 144 Bytes)
2: 1.001263 Sekunden (5 Allokationen: 144 Bytes)
3: 1.003676 Sekunden (5 Allokationen: 144 Bytes)
```
