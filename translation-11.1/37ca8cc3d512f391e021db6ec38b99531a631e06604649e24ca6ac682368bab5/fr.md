```
Base.identify_package(name::String)::Union{PkgId, Nothing}
Base.identify_package(where::Union{Module,PkgId}, name::String)::Union{PkgId, Nothing}
```

Identifiez le package par son nom à partir de la pile d'environnement actuelle, renvoyant son `PkgId`, ou `nothing` s'il ne peut pas être trouvé.

Si seul l'argument `name` est fourni, il recherche dans chaque environnement de la pile et ses dépendances directes nommées.

L'argument `where` fournit le contexte à partir duquel rechercher le package : dans ce cas, il vérifie d'abord si le nom correspond au contexte lui-même, sinon il recherche toutes les dépendances récursives (à partir du manifeste résolu de chaque environnement) jusqu'à ce qu'il localise le contexte `where`, et à partir de là identifie la dépendance avec le nom correspondant.

```julia-repl
julia> Base.identify_package("Pkg") # Pkg est une dépendance de l'environnement par défaut
Pkg [44cfe95a-1eb2-52ea-b672-e2afdf69b78f]

julia> using LinearAlgebra

julia> Base.identify_package(LinearAlgebra, "Pkg") # Pkg n'est pas une dépendance de LinearAlgebra
```
