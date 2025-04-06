```
evalfile(path::AbstractString, args::Vector{String}=String[])
```

Charge le fichier dans un module anonyme en utilisant [`include`](@ref), évalue toutes les expressions et retourne la valeur de la dernière expression. L'argument optionnel `args` peut être utilisé pour définir les arguments d'entrée du script (c'est-à-dire la variable globale `ARGS`). Notez que les définitions (par exemple, méthodes, globales) sont évaluées dans le module anonyme et n'affectent pas le module actuel.

# Exemples

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
