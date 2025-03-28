```
annotations(str::Union{AnnotatedString, SubString{AnnotatedString}},
            [position::Union{Integer, UnitRange}]) ->
    Vector{@NamedTuple{region::UnitRange{Int64}, label::Symbol, value}}

Obtén todas las anotaciones que se aplican a `str`. Si se proporciona `position`, solo se devolverán las anotaciones que se superpongan con `position`.

Las anotaciones se proporcionan junto con las regiones a las que se aplican, en forma de un vector de tuplas de región-anotación.

De acuerdo con la semántica documentada en [`AnnotatedString`](@ref), el orden de las anotaciones devueltas coincide con el orden en que se aplicaron.

Ver también: [`annotate!`](@ref).
```
