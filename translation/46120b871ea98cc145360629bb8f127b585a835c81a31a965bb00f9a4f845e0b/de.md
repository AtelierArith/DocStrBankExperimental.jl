```
evalfile(path::AbstractString, args::Vector{String}=String[])
```

Lädt die Datei in ein anonymes Modul mit [`include`](@ref), bewertet alle Ausdrücke und gibt den Wert des letzten Ausdrucks zurück. Das optionale Argument `args` kann verwendet werden, um die Eingabeargumente des Skripts festzulegen (d.h. die globale `ARGS`-Variable). Beachten Sie, dass Definitionen (z.B. Methoden, globale Variablen) im anonymen Modul ausgewertet werden und das aktuelle Modul nicht beeinflussen.

# Beispiele

```jldoctest
julia> write("testfile.jl", """
           @show ARGS
           1 + 1
       """);

julia> x = evalfile("testfile.jl", ["ARG1", "ARG2"]);
ARGS = ["ARG1", "ARG2"]

julia> x
2

julia> rm("testfile.jl")
```
