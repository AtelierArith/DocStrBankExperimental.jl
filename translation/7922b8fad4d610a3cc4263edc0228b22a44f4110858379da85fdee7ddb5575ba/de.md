```
titlecase(s::AbstractString; [wordsep::Function], strict::Bool=true) -> String
```

Kapitalisiere das erste Zeichen jedes Wortes in `s`; wenn `strict` wahr ist, wird jedes andere Zeichen in Kleinbuchstaben umgewandelt, andernfalls bleiben sie unverändert. Standardmäßig werden alle Nicht-Buchstaben, die ein neues Graphem beginnen, als Worttrennzeichen betrachtet; ein Prädikat kann als Schlüsselwort `wordsep` übergeben werden, um zu bestimmen, welche Zeichen als Worttrennzeichen betrachtet werden sollen. Siehe auch [`uppercasefirst`](@ref), um nur das erste Zeichen in `s` zu kapitalisieren.

Siehe auch [`uppercase`](@ref), [`lowercase`](@ref), [`uppercasefirst`](@ref).

# Beispiele

```jldoctest
julia> titlecase("the JULIA programming language")
"The Julia Programming Language"

julia> titlecase("ISS - international space station", strict=false)
"ISS - International Space Station"

julia> titlecase("a-a b-b", wordsep = c->c==' ')
"A-a B-b"
```
