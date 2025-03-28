```
pkgdir(m::Module[, paths::String...])
```

Renvoie le répertoire racine du package qui a déclaré le module `m`, ou `nothing` si `m` n'a pas été déclaré dans un package. Des chaînes de composants de chemin supplémentaires peuvent être fournies pour construire un chemin dans le répertoire racine du package.

Pour obtenir le répertoire racine du package qui implémente le module actuel, la forme `pkgdir(@__MODULE__)` peut être utilisée.

Si un module d'extension est donné, la racine du package parent est renvoyée.

```julia-repl
julia> pkgdir(Foo)
"/path/to/Foo.jl"

julia> pkgdir(Foo, "src", "file.jl")
"/path/to/Foo.jl/src/file.jl"
```

Voir aussi [`pathof`](@ref).

!!! compat "Julia 1.7"
    L'argument optionnel `paths` nécessite au moins Julia 1.7.

