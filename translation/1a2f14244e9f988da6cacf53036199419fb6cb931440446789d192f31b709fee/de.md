```
peel([T,] ref::GitReference)
```

Rekursiv `ref` abblättern, bis ein Objekt vom Typ `T` erhalten wird. Wenn kein `T` angegeben ist, wird `ref` abblättern, bis ein Objekt erhalten wird, das kein [`GitTag`](@ref) ist.

  * Ein `GitTag` wird auf das Objekt abblättern, auf das es verweist.
  * Ein [`GitCommit`](@ref) wird auf einen [`GitTree`](@ref) abblättern.

!!! note
    Nur annotierte Tags können auf `GitTag`-Objekte abblättern. Leichte Tags (der Standard) sind Referenzen unter `refs/tags/`, die direkt auf `GitCommit`-Objekte zeigen.

