```
unsafe_replace!(p::Ptr{T}, expected, desired,
               [success_order::Symbol[, fail_order::Symbol=success_order]]) -> (; old, success::Bool)
```

Diese führen atomar die Operationen aus, um eine Speicheradresse auf einen gegebenen Wert zu erhalten und bedingt zu setzen. Wenn von der Hardware unterstützt, kann dies auf die entsprechende Hardwareanweisung optimiert werden, andernfalls wird die Ausführung ähnlich sein wie:

```
y = unsafe_load(p, fail_order)
ok = y === expected
if ok
    unsafe_store!(p, desired, success_order)
end
return (; old = y, success = ok)
```

Das `unsafe`-Präfix bei dieser Funktion zeigt an, dass keine Validierung des Zeigers `p` durchgeführt wird, um sicherzustellen, dass er gültig ist. Wie in C ist der Programmierer dafür verantwortlich, sicherzustellen, dass der referenzierte Speicher nicht freigegeben oder garbage collected wird, während diese Funktion aufgerufen wird. Falsche Verwendung kann zu einem Segfault in Ihrem Programm führen.

!!! compat "Julia 1.10"
    Diese Funktion erfordert mindestens Julia 1.10.


Siehe auch: [`replaceproperty!`](@ref Base.replaceproperty!), [`atomic`](@ref)
