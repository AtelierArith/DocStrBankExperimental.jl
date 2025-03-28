```
AnnotatedString{S <: AbstractString} <: AbstractString
```

Une chaîne avec des métadonnées, sous la forme de régions annotées.

Plus précisément, il s'agit d'un simple wrapper autour de toute autre [`AbstractString`](@ref) qui permet d'annoter des régions de la chaîne enveloppée avec des valeurs étiquetées.

```text
                           C
                    ┌──────┸─────────┐
  "this is an example annotated string"
  └──┰────────┼─────┘         │
     A        └─────┰─────────┘
                    B
```

Le diagramme ci-dessus représente un `AnnotatedString` où trois plages ont été annotées (étiquetées `A`, `B` et `C`). Chaque annotation contient une étiquette (`Symbol`) et une valeur (`Any`). Ces trois morceaux d'information sont conservés sous la forme d'un `@NamedTuple{region::UnitRange{Int64}, label::Symbol, value}`.

Les étiquettes n'ont pas besoin d'être uniques, la même région peut contenir plusieurs annotations avec la même étiquette.

Le code écrit pour les `AnnotatedString`s en général doit conserver les propriétés suivantes :

  * Quels caractères une annotation est appliquée
  * L'ordre dans lequel les annotations sont appliquées à chaque caractère

Des sémantiques supplémentaires peuvent être introduites par des utilisations spécifiques des `AnnotatedString`s.

Un corollaire de ces règles est que des annotations adjacentes, placées consécutivement, avec des étiquettes et des valeurs identiques sont équivalentes à une seule annotation s'étendant sur la plage combinée.

Voir aussi [`AnnotatedChar`](@ref), [`annotatedstring`](@ref), [`annotations`](@ref), et [`annotate!`](@ref).

# Constructeurs

```julia
AnnotatedString(s::S<:AbstractString) -> AnnotatedString{S}
AnnotatedString(s::S<:AbstractString, annotations::Vector{@NamedTuple{region::UnitRange{Int64}, label::Symbol, value}})
```

Un AnnotatedString peut également être créé avec [`annotatedstring`](@ref), qui fonctionne beaucoup comme [`string`](@ref) mais préserve toutes les annotations présentes dans les arguments.

# Exemples

```julia-repl
julia> AnnotatedString("this is an example annotated string",
                    [(1:18, :A => 1), (12:28, :B => 2), (18:35, :C => 3)])
"this is an example annotated string"
```
