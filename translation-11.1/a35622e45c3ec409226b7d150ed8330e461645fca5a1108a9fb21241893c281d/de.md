```
annotations(str::Union{AnnotatedString, SubString{AnnotatedString}},
            [position::Union{Integer, UnitRange}]) ->
    Vector{@NamedTuple{region::UnitRange{Int64}, label::Symbol, value}}

Erhalten Sie alle Annotationen, die auf `str` zutreffen. Sollte `position` angegeben werden, werden nur Annotationen zurückgegeben, die sich mit `position` überschneiden.

Annotationen werden zusammen mit den Regionen, auf die sie zutreffen, in Form eines Vektors von Region-Annotation-Tupeln bereitgestellt.

In Übereinstimmung mit der in [`AnnotatedString`](@ref) dokumentierten Semantik entspricht die Reihenfolge der zurückgegebenen Annotationen der Reihenfolge, in der sie angewendet wurden.

Siehe auch: [`annotate!`](@ref).
```
