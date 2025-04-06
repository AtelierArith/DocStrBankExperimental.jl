```
annotatedstring(values...)
```

Crea un `AnnotatedString` a partir de cualquier número de `values` utilizando su representación [`print`](@ref).

Esto actúa como [`string`](@ref), pero se encarga de preservar cualquier anotación presente (en forma de valores [`AnnotatedString`](@ref) o [`AnnotatedChar`](@ref)).

Véase también [`AnnotatedString`](@ref) y [`AnnotatedChar`](@ref).

## Ejemplos

```julia-repl
julia> annotatedstring("now a AnnotatedString")
"now a AnnotatedString"

julia> annotatedstring(AnnotatedString("annotated", [(1:9, :label => 1)]), ", and unannotated")
"annotated, and unannotated"
```
