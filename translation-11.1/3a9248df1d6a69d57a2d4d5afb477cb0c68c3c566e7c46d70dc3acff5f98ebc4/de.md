```
Colon()
```

Doppelpunkt (:) werden verwendet, um das Indizieren ganzer Objekte oder Dimensionen auf einmal zu kennzeichnen.

Sehr wenige Operationen sind direkt auf Doppelpunkt definiert; stattdessen werden sie durch [`to_indices`](@ref) in einen internen Vektortyp (`Base.Slice`) umgewandelt, um die Sammlung von Indizes darzustellen, die sie abdecken, bevor sie verwendet werden.

Die Singleton-Instanz von `Colon` ist auch eine Funktion, die verwendet wird, um Bereiche zu konstruieren; siehe [`:`](@ref).
