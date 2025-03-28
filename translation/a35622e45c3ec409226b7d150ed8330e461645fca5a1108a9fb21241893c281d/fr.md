```
annotations(str::Union{AnnotatedString, SubString{AnnotatedString}},
            [position::Union{Integer, UnitRange}]) ->
    Vector{@NamedTuple{region::UnitRange{Int64}, label::Symbol, value}}

Obtenez toutes les annotations qui s'appliquent à `str`. Si `position` est fourni, seules les annotations qui se chevauchent avec `position` seront retournées.

Les annotations sont fournies avec les régions auxquelles elles s'appliquent, sous la forme d'un vecteur de tuples région-annotation.

Conformément à la sémantique documentée dans [`AnnotatedString`](@ref), l'ordre des annotations retournées correspond à l'ordre dans lequel elles ont été appliquées.

Voir aussi : [`annotate!`](@ref).
```
