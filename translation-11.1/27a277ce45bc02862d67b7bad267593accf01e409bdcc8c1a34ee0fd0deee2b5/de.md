```
splitpath(path::AbstractString) -> Vector{String}
```

Teile einen Dateipfad in alle seine Pfadkomponenten auf. Dies ist das Gegenteil von `joinpath`. Gibt ein Array von Teilstrings zurück, eines für jedes Verzeichnis oder jede Datei im Pfad, einschließlich des Wurzelverzeichnisses, falls vorhanden.

!!! compat "Julia 1.1"
    Diese Funktion erfordert mindestens Julia 1.1.


# Beispiele

```jldoctest
julia> splitpath("/home/myuser/example.jl")
4-element Vector{String}:
 "/"
 "home"
 "myuser"
 "example.jl"
```
