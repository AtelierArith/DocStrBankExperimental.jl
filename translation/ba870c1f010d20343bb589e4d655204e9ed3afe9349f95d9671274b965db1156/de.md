```
basename(path::AbstractString) -> String
```

Holen Sie sich den Dateinamensteil eines Pfades.

!!! Hinweis     Diese Funktion unterscheidet sich leicht vom Unix-Programm `basename`, bei dem abschließende Schrägstriche ignoriert werden, d.h. `$ basename /foo/bar/` gibt `bar` zurück, während `basename` in Julia einen leeren String `""` zurückgibt.

# Beispiele

```jldoctest
julia> basename("/home/myuser/example.jl")
"example.jl"

julia> basename("/home/myuser/")
""
```

Siehe auch [`dirname`](@ref).
