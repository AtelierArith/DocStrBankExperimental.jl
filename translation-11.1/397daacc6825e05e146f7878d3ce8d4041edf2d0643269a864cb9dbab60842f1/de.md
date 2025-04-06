```
CachingPool(workers::Vector{Int})
```

Eine Implementierung eines `AbstractWorkerPool`. [`remote`](@ref), [`remotecall_fetch`](@ref), [`pmap`](@ref) (und andere Remoteaufrufe, die Funktionen remote ausführen) profitieren davon, die serialisierten/deserialisierten Funktionen auf den Arbeitsknoten zwischenzuspeichern, insbesondere Closures (die große Datenmengen erfassen können).

Der Remote-Cache wird für die Lebensdauer des zurückgegebenen `CachingPool`-Objekts aufrechterhalten. Um den Cache früher zu leeren, verwenden Sie `clear!(pool)`.

Für globale Variablen werden nur die Bindungen in einem Closure erfasst, nicht die Daten. `let`-Blöcke können verwendet werden, um globale Daten zu erfassen.

# Beispiele

```julia
const foo = rand(10^8);
wp = CachingPool(workers())
let foo = foo
    pmap(i -> sum(foo) + i, wp, 1:100);
end
```

Das obige würde `foo` nur einmal an jeden Arbeiter übertragen.
