```
unsafe_swap!(p::Ptr{T}, x, [order::Symbol])
```

Diese führen atomar die Operationen aus, um gleichzeitig eine Speicheradresse zu lesen und zu setzen. Wenn dies von der Hardware unterstützt wird, kann es auf die entsprechende Hardwareanweisung optimiert werden, andernfalls wird die Ausführung ähnlich sein wie:

```
y = unsafe_load(p)
unsafe_store!(p, x)
return y
```

Das `unsafe`-Präfix bei dieser Funktion zeigt an, dass keine Validierung des Zeigers `p` durchgeführt wird, um sicherzustellen, dass er gültig ist. Wie in C ist der Programmierer dafür verantwortlich, sicherzustellen, dass der referenzierte Speicher nicht freigegeben oder garbage collected wird, während diese Funktion aufgerufen wird. Falsche Verwendung kann zu einem Segfault in Ihrem Programm führen.

!!! compat "Julia 1.10"
    Diese Funktion erfordert mindestens Julia 1.10.


Siehe auch: [`swapproperty!`](@ref Base.swapproperty!), [`atomic`](@ref)
