```
RegexMatch <: AbstractMatch
```

Ein Typ, der ein einzelnes Match zu einem [`Regex`](@ref) darstellt, das in einem String gefunden wurde. Typischerweise erstellt aus der [`match`](@ref) Funktion.

Das Feld `match` speichert den Teilstring des gesamten übereinstimmenden Strings. Das Feld `captures` speichert die Teilstrings für jede Capture-Gruppe, indiziert nach Nummer. Um nach dem Namen der Capture-Gruppe zu indizieren, sollte stattdessen das gesamte Match-Objekt indiziert werden, wie in den Beispielen gezeigt. Der Standort des Beginns des Matches wird im Feld `offset` gespeichert. Das Feld `offsets` speichert die Standorte des Beginns jeder Capture-Gruppe, wobei 0 eine Gruppe bezeichnet, die nicht erfasst wurde.

Dieser Typ kann als Iterator über die Capture-Gruppen des `Regex` verwendet werden, der die in jeder Gruppe erfassten Teilstrings liefert. Aufgrund dessen können die Erfassungen eines Matches destrukturiert werden. Wenn eine Gruppe nicht erfasst wurde, wird stattdessen `nothing` anstelle eines Teilstrings zurückgegeben.

Methoden, die ein `RegexMatch`-Objekt akzeptieren, sind definiert für [`iterate`](@ref), [`length`](@ref), [`eltype`](@ref), [`keys`](@ref keys(::RegexMatch)), [`haskey`](@ref), und [`getindex`](@ref), wobei die Schlüssel die Namen oder Nummern einer Capture-Gruppe sind. Siehe [`keys`](@ref keys(::RegexMatch)) für weitere Informationen.

# Beispiele

```jldoctest
julia> m = match(r"(?<hour>\d+):(?<minute>\d+)(am|pm)?", "11:30 in the morning")
RegexMatch("11:30", hour="11", minute="30", 3=nothing)

julia> m.match
"11:30"

julia> m.captures
3-element Vector{Union{Nothing, SubString{String}}}:
 "11"
 "30"
 nothing


julia> m["minute"]
"30"

julia> hr, min, ampm = m; # destrukturiere Capture-Gruppen durch Iteration

julia> hr
"11"
```
