```
broadcast(f, As...)
```

Übertrage die Funktion `f` über die Arrays, Tupel, Sammlungen, [`Ref`](@ref)s und/oder Skalare `As`.

Das Broadcasting wendet die Funktion `f` auf die Elemente der Container-Argumente und die Skalare selbst in `As` an. Singleton- und fehlende Dimensionen werden erweitert, um den Ausdehnungen der anderen Argumente zu entsprechen, indem der Wert virtuell wiederholt wird. Standardmäßig werden nur eine begrenzte Anzahl von Typen als Skalare betrachtet, einschließlich `Number`s, `String`s, `Symbol`s, `Type`s, `Function`s und einigen gängigen Singletons wie [`missing`](@ref) und [`nothing`](@ref). Alle anderen Argumente werden elementweise durchlaufen oder indiziert.

Der resultierende Containertyp wird durch die folgenden Regeln festgelegt:

  * Wenn alle Argumente Skalare oder nulldimensionale Arrays sind, gibt es ein entpacktes Skalar zurück.
  * Wenn mindestens ein Argument ein Tupel ist und alle anderen Skalare oder nulldimensionale Arrays sind, gibt es ein Tupel zurück.
  * Alle anderen Kombinationen von Argumenten geben standardmäßig ein `Array` zurück, aber benutzerdefinierte Containertypen können ihre eigene Implementierung und ähnliche Regeln zur Förderung definieren, um das Ergebnis anzupassen, wenn sie als Argumente erscheinen.

Es gibt eine spezielle Syntax für das Broadcasting: `f.(args...)` ist äquivalent zu `broadcast(f, args...)`, und verschachtelte `f.(g.(args...))`-Aufrufe werden in eine einzige Broadcast-Schleife zusammengeführt.

# Beispiele

```jldoctest
julia> A = [1, 2, 3, 4, 5]
5-element Vector{Int64}:
 1
 2
 3
 4
 5

julia> B = [1 2; 3 4; 5 6; 7 8; 9 10]
5×2 Matrix{Int64}:
 1   2
 3   4
 5   6
 7   8
 9  10

julia> broadcast(+, A, B)
5×2 Matrix{Int64}:
  2   3
  5   6
  8   9
 11  12
 14  15

julia> parse.(Int, ["1", "2"])
2-element Vector{Int64}:
 1
 2

julia> abs.((1, -2))
(1, 2)

julia> broadcast(+, 1.0, (0, -2.0))
(1.0, -1.0)

julia> (+).([[0,2], [1,3]], Ref{Vector{Int}}([1,-1]))
2-element Vector{Vector{Int64}}:
 [1, 1]
 [2, 2]

julia> string.(("one","two","three","four"), ": ", 1:4)
4-element Vector{String}:
 "one: 1"
 "two: 2"
 "three: 3"
 "four: 4"

```
