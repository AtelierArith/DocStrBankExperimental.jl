```
Tuple{Types...}
```

Ein Tupel ist ein Container fester Länge, der beliebige Werte unterschiedlicher Typen halten kann, aber nicht modifiziert werden kann (es ist unveränderlich). Die Werte können über Indizes zugegriffen werden. Tupel-Literale werden mit Kommas und Klammern geschrieben:

```jldoctest
julia> (1, 1+1)
(1, 2)

julia> (1,)
(1,)

julia> x = (0.0, "hello", 6*7)
(0.0, "hello", 42)

julia> x[2]
"hello"

julia> typeof(x)
Tuple{Float64, String, Int64}
```

Ein Tupel der Länge 1 muss mit einem Komma geschrieben werden, `(1,)`, da `(1)` nur einen in Klammern gesetzten Wert darstellen würde. `()` repräsentiert das leere (Länge-0) Tupel.

Ein Tupel kann aus einem Iterator konstruiert werden, indem ein `Tuple`-Typ als Konstruktor verwendet wird:

```jldoctest
julia> Tuple(["a", 1])
("a", 1)

julia> Tuple{String, Float64}(["a", 1])
("a", 1.0)
```

Tupeltypen sind in ihren Parametern kovariant: `Tuple{Int}` ist ein Subtyp von `Tuple{Any}`. Daher wird `Tuple{Any}` als abstrakter Typ betrachtet, und Tupeltypen sind nur konkret, wenn ihre Parameter es sind. Tupel haben keine Feldnamen; Felder werden nur über Indizes zugegriffen. Tupeltypen können beliebig viele Parameter haben.

Siehe den Handbuchabschnitt über [Tuple Types](@ref).

Siehe auch [`Vararg`](@ref), [`NTuple`](@ref), [`ntuple`](@ref), [`tuple`](@ref), [`NamedTuple`](@ref).
