# Module loading

[`Base.require`](@ref) est responsable du chargement des modules et gère également le cache de précompilation. C'est l'implémentation de l'instruction `import`.

## Experimental features

Les fonctionnalités ci-dessous sont expérimentales et ne font pas partie de l'API stable de Julia. Avant de les utiliser, renseignez-vous sur la réflexion actuelle et sur la possibilité qu'elles changent bientôt.

### Package loading callbacks

Il est possible d'écouter les packages chargés par `Base.require`, en enregistrant un rappel.

```julia
loaded_packages = Base.PkgId[]
callback = (pkg::Base.PkgId) -> push!(loaded_packages, pkg)
push!(Base.package_callbacks, callback)
```

L'utilisation de ceci ressemblerait à :

```julia-repl
julia> using Example

julia> loaded_packages
1-element Vector{Base.PkgId}:
 Example [7876af07-990d-54b4-ab0e-23690620f79a]
```
