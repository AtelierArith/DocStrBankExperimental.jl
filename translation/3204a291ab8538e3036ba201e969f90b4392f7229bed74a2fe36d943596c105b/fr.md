```
@__DIR__ -> String
```

Macro pour obtenir le chemin absolu du répertoire actuel sous forme de chaîne.

S'il est utilisé dans un script, renvoie le répertoire du script contenant l'appel de macro `@__DIR__`. S'il est exécuté depuis un REPL ou s'il est évalué par `julia -e <expr>`, renvoie le répertoire de travail actuel.

# Exemples

L'exemple illustre la différence de comportement entre `@__DIR__` et `pwd()`, en créant un script simple dans un répertoire différent de celui de travail actuel et en exécutant les deux commandes :

```julia-repl
julia> cd("/home/JuliaUser") # répertoire de travail

julia> # créer un script à /home/JuliaUser/Projects
       open("/home/JuliaUser/Projects/test.jl","w") do io
           print(io, """
               println("@__DIR__ = ", @__DIR__)
               println("pwd() = ", pwd())
           """)
       end

julia> # affiche le répertoire du script et le répertoire de travail actuel
       include("/home/JuliaUser/Projects/test.jl")
@__DIR__ = /home/JuliaUser/Projects
pwd() = /home/JuliaUser
```
