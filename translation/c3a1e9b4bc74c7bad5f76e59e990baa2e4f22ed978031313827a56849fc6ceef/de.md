```
copy!(dst, src) -> dst
```

In-place [`copy`](@ref) von `src` nach `dst`, wobei alle vorhandenen Elemente in `dst` verworfen werden. Wenn `dst` und `src` vom gleichen Typ sind, sollte nach dem Aufruf `dst == src` gelten. Wenn `dst` und `src` mehrdimensionale Arrays sind, müssen sie gleiche [`axes`](@ref) haben.

!!! warning
    Das Verhalten kann unerwartet sein, wenn ein veränderter Parameter Speicher mit einem anderen Parameter teilt.


Siehe auch [`copyto!`](@ref).

!!! compat "Julia 1.1"
    Diese Methode erfordert mindestens Julia 1.1. In Julia 1.0 ist diese Methode aus der `Future`-Standardbibliothek als `Future.copy!` verfügbar.

