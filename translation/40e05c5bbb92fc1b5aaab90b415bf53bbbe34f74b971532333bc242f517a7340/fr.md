```
annotatedstring(values...)
```

Crée un `AnnotatedString` à partir de n'importe quel nombre de `values` en utilisant leur représentation [`print`](@ref)ée.

Cela fonctionne comme [`string`](@ref), mais prend soin de préserver toutes les annotations présentes (sous la forme de valeurs [`AnnotatedString`](@ref) ou [`AnnotatedChar`](@ref)).

Voir aussi [`AnnotatedString`](@ref) et [`AnnotatedChar`](@ref).

## Exemples

```julia-repl
julia> annotatedstring("now a AnnotatedString")
"now a AnnotatedString"

julia> annotatedstring(AnnotatedString("annotated", [(1:9, :label => 1)]), ", and unannotated")
"annotated, and unannotated"
```
