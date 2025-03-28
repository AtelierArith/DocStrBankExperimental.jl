```
lock(f::Function, lock)
```

Erwirbt das `lock`, führt `f` mit dem gehaltenen `lock` aus und gibt das `lock` frei, wenn `f` zurückkehrt. Wenn das `lock` bereits von einer anderen Aufgabe/Thread gesperrt ist, wird gewartet, bis es verfügbar wird.

Wenn diese Funktion zurückkehrt, wurde das `lock` freigegeben, sodass der Aufrufer nicht versuchen sollte, es zu `unlock`.

Siehe auch: [`@lock`](@ref).

!!! compat "Julia 1.7"
    Die Verwendung eines [`Channel`](@ref) als zweiten Parameter erfordert Julia 1.7 oder höher.

