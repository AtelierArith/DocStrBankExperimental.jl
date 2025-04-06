```
annotatedstring(values...)
```

Erstellt eine `AnnotatedString` aus beliebig vielen `values` unter Verwendung ihrer [`print`](@ref)ed Darstellung.

Dies funktioniert wie [`string`](@ref), sorgt jedoch dafür, dass alle vorhandenen Anmerkungen (in Form von [`AnnotatedString`](@ref) oder [`AnnotatedChar`](@ref) Werten) erhalten bleiben.

Siehe auch [`AnnotatedString`](@ref) und [`AnnotatedChar`](@ref).

## Beispiele

```julia-repl
julia> annotatedstring("now a AnnotatedString")
"now a AnnotatedString"

julia> annotatedstring(AnnotatedString("annotated", [(1:9, :label => 1)]), ", and unannotated")
"annotated, and unannotated"
```
