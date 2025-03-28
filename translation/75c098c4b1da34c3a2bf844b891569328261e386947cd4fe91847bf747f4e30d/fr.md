```
normpath(path::AbstractString) -> String
```

Normaliser un chemin, en supprimant les entrées "." et ".." et en changeant "/" par le séparateur de chemin canonique pour le système.

# Exemples

```jldoctest
julia> normpath("/home/myuser/../example.jl")
"/home/example.jl"

julia> normpath("Documents/Julia") == joinpath("Documents", "Julia")
true
```
