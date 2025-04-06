```
AnnotatedString{S <: AbstractString} <: AbstractString
```

Ein String mit Metadaten, in Form von annotierten Regionen.

Genauer gesagt, ist dies ein einfacher Wrapper um jeden anderen [`AbstractString`](@ref), der es ermöglicht, Regionen des umschlossenen Strings mit beschrifteten Werten zu annotieren.

```text
                           C
                    ┌──────┸─────────┐
  "this is an example annotated string"
  └──┰────────┼─────┘         │
     A        └─────┰─────────┘
                    B
```

Das obige Diagramm stellt ein `AnnotatedString` dar, bei dem drei Bereiche annotiert wurden (beschriftet mit `A`, `B` und `C`). Jede Annotation enthält ein Label (`Symbol`) und einen Wert (`Any`). Diese drei Informationen werden als `@NamedTuple{region::UnitRange{Int64}, label::Symbol, value}` gehalten.

Labels müssen nicht einzigartig sein, dieselbe Region kann mehrere Annotationen mit demselben Label enthalten.

Code, der für `AnnotatedString`s im Allgemeinen geschrieben wird, sollte die folgenden Eigenschaften bewahren:

  * Auf welche Zeichen eine Annotation angewendet wird
  * Die Reihenfolge, in der Annotationen auf jedes Zeichen angewendet werden

Zusätzliche Semantiken können durch spezifische Verwendungen von `AnnotatedString`s eingeführt werden.

Eine Folgerung dieser Regeln ist, dass benachbarte, nacheinander platzierte Annotationen mit identischen Labels und Werten äquivalent zu einer einzelnen Annotation sind, die den kombinierten Bereich umfasst.

Siehe auch [`AnnotatedChar`](@ref), [`annotatedstring`](@ref), [`annotations`](@ref) und [`annotate!`](@ref).

# Konstruktoren

```julia
AnnotatedString(s::S<:AbstractString) -> AnnotatedString{S}
AnnotatedString(s::S<:AbstractString, annotations::Vector{@NamedTuple{region::UnitRange{Int64}, label::Symbol, value}})
```

Ein AnnotatedString kann auch mit [`annotatedstring`](@ref) erstellt werden, das ähnlich wie [`string`](@ref) funktioniert, aber alle in den Argumenten vorhandenen Annotationen beibehält.

# Beispiele

```julia-repl
julia> AnnotatedString("this is an example annotated string",
                    [(1:18, :A => 1), (12:28, :B => 2), (18:35, :C => 3)])
"this is an example annotated string"
```
