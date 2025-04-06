```
@__DIR__ -> String
```

Makro, um den absoluten Pfad des aktuellen Verzeichnisses als String zu erhalten.

Wenn in einem Skript, gibt das Verzeichnis des Skripts zurück, das den `@__DIR__`-Makroaufruf enthält. Wenn es von einem REPL ausgeführt wird oder wenn es mit `julia -e <expr>` ausgewertet wird, gibt es das aktuelle Arbeitsverzeichnis zurück.

# Beispiele

Das Beispiel veranschaulicht den Unterschied im Verhalten von `@__DIR__` und `pwd()`, indem ein einfaches Skript in einem anderen Verzeichnis als dem aktuellen Arbeitsverzeichnis erstellt und beide Befehle ausgeführt werden:

```julia-repl
julia> cd("/home/JuliaUser") # Arbeitsverzeichnis

julia> # Skript unter /home/JuliaUser/Projects erstellen
       open("/home/JuliaUser/Projects/test.jl","w") do io
           print(io, """
               println("@__DIR__ = ", @__DIR__)
               println("pwd() = ", pwd())
           """)
       end

julia> # gibt das Skriptverzeichnis und das aktuelle Arbeitsverzeichnis aus
       include("/home/JuliaUser/Projects/test.jl")
@__DIR__ = /home/JuliaUser/Projects
pwd() = /home/JuliaUser
```
