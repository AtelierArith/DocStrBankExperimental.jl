```
LazyString <: AbstractString
```

Eine faule Darstellung der String-Interpolation. Dies ist nützlich, wenn ein String in einem Kontext konstruiert werden muss, in dem die tatsächliche Interpolation und String-Konstruktion unnötig oder unerwünscht ist (z. B. in Fehlerpfaden von Funktionen).

Dieser Typ ist so konzipiert, dass er zur Laufzeit kostengünstig zu konstruieren ist und versucht, so viel Arbeit wie möglich entweder auf das Makro oder auf spätere Druckoperationen zu verlagern.

# Beispiele

```jldoctest
julia> n = 5; str = LazyString("n ist ", n)
"n ist 5"
```

Siehe auch [`@lazy_str`](@ref).

!!! compat "Julia 1.8"
    `LazyString` erfordert Julia 1.8 oder höher.


# Erweiterte Hilfe

## Sicherheitsmerkmale für nebenläufige Programme

Ein fauler String selbst führt nicht zu Nebenläufigkeitsproblemen, selbst wenn er in mehreren Julia-Aufgaben gedruckt wird. Wenn jedoch `print`-Methoden auf einem erfassten Wert ohne Synchronisationen aufgerufen werden, kann es bei der Ausgabe des faulen Strings zu Problemen kommen. Darüber hinaus können die `print`-Methoden auf den erfassten Werten mehrmals aufgerufen werden, obwohl nur genau ein Ergebnis zurückgegeben wird.

!!! compat "Julia 1.9"
    `LazyString` ist in diesem Sinne in Julia 1.9 und höher sicher.

