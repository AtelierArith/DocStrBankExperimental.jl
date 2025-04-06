```
unsafe_modify!(p::Ptr{T}, op, x, [order::Symbol]) -> Pair
```

Diese führen atomar die Operationen aus, um eine Speicheradresse zu lesen und zu setzen, nachdem die Funktion `op` angewendet wurde. Wenn dies von der Hardware unterstützt wird (zum Beispiel atomare Inkrementierung), kann dies auf die entsprechende Hardwareanweisung optimiert werden, andernfalls wird die Ausführung ähnlich sein wie:

```
y = unsafe_load(p)
z = op(y, x)
unsafe_store!(p, z)
return y => z
```

Das `unsafe`-Präfix bei dieser Funktion zeigt an, dass keine Validierung des Zeigers `p` durchgeführt wird, um sicherzustellen, dass er gültig ist. Wie in C ist der Programmierer dafür verantwortlich, sicherzustellen, dass der referenzierte Speicher nicht freigegeben oder garbage collected wird, während diese Funktion aufgerufen wird. Falsche Verwendung kann zu einem Segfault in Ihrem Programm führen.

!!! compat "Julia 1.10"
    Diese Funktion erfordert mindestens Julia 1.10.


Siehe auch: [`modifyproperty!`](@ref Base.modifyproperty!), [`atomic`](@ref)
