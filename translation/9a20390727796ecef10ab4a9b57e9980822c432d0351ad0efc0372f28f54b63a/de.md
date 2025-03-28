```
Random.default_rng() -> rng
```

Gibt den standardmäßigen globalen Zufallszahlengenerator (RNG) zurück, der von `rand`-bezogenen Funktionen verwendet wird, wenn kein expliziter RNG bereitgestellt wird.

Wenn das `Random`-Modul geladen wird, wird der standardmäßige RNG *zufällig* initialisiert, über [`Random.seed!()`](@ref): das bedeutet, dass bei jedem Start einer neuen Julia-Sitzung der erste Aufruf von `rand()` ein anderes Ergebnis liefert, es sei denn, `seed!(seed)` wird zuerst aufgerufen.

Es ist threadsicher: Verschiedene Threads können sicher `rand`-bezogene Funktionen auf `default_rng()` gleichzeitig aufrufen, z. B. `rand(default_rng())`.

!!! note
    Der Typ des standardmäßigen RNG ist ein Implementierungsdetail. In verschiedenen Versionen von Julia sollten Sie nicht erwarten, dass der standardmäßige RNG immer denselben Typ hat, noch dass er für einen gegebenen Seed denselben Strom von Zufallszahlen erzeugt.


!!! compat "Julia 1.3"
    Diese Funktion wurde in Julia 1.3 eingeführt.

