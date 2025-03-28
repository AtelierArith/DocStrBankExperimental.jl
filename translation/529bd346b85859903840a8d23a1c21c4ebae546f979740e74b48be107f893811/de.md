```
==(a::AbstractString, b::AbstractString) -> Bool
```

Überprüfen, ob zwei Strings zeichenweise (technisch gesehen, Unicode-Codepunkt für Codepunkt) gleich sind. Sollten einer der Strings ein [`AnnotatedString`](@ref) sein, müssen auch die String-Eigenschaften übereinstimmen.

# Beispiele

```jldoctest
julia> "abc" == "abc"
true

julia> "abc" == "αβγ"
false
```
