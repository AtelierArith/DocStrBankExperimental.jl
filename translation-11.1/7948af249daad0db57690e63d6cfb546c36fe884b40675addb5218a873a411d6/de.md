```
unsafe_load(p::Ptr{T}, i::Integer=1)
unsafe_load(p::Ptr{T}, order::Symbol)
unsafe_load(p::Ptr{T}, i::Integer, order::Symbol)
```

Lädt einen Wert des Typs `T` von der Adresse des `i`-ten Elements (1-indiziert), beginnend bei `p`. Dies entspricht dem C-Ausdruck `p[i-1]`. Optional kann eine atomare Speicherreihenfolge angegeben werden.

Das Präfix `unsafe` bei dieser Funktion zeigt an, dass keine Validierung des Zeigers `p` durchgeführt wird, um sicherzustellen, dass er gültig ist. Wie in C ist der Programmierer dafür verantwortlich, sicherzustellen, dass der referenzierte Speicher nicht freigegeben oder garbage collected wird, während diese Funktion aufgerufen wird. Falsche Verwendung kann zu einem Segfault Ihres Programms führen oder fehlerhafte Antworten zurückgeben. Im Gegensatz zu C kann das Dereferenzieren eines Speicherbereichs, der als anderer Typ zugewiesen wurde, gültig sein, vorausgesetzt, die Typen sind kompatibel.

!!! compat "Julia 1.10"
    Das Argument `order` ist seit Julia 1.10 verfügbar.


Siehe auch: [`atomic`](@ref)
