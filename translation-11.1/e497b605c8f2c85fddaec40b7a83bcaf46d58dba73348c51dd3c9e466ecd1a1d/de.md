```
uppercasefirst(s::AbstractString) -> String
```

Gibt `s` mit dem ersten Zeichen in Großbuchstaben zurück (technisch "Titelcase" für Unicode). Siehe auch [`titlecase`](@ref), um das erste Zeichen jedes Wortes in `s` zu kapitalisieren.

Siehe auch [`lowercasefirst`](@ref), [`uppercase`](@ref), [`lowercase`](@ref), [`titlecase`](@ref).

# Beispiele

```jldoctest
julia> uppercasefirst("python")
"Python"
```
