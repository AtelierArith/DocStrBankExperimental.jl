```
normpath(path::AbstractString) -> String
```

Normalisiert einen Pfad, entfernt "." und ".." Einträge und ändert "/" in den kanonischen Pfadtrennzeichen für das System.

# Beispiele

```jldoctest
julia> normpath("/home/myuser/../example.jl")
"/home/example.jl"

julia> normpath("Documents/Julia") == joinpath("Documents", "Julia")
true
```
