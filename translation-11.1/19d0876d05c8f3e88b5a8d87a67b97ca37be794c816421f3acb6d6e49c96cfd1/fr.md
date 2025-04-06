```
LibGit2.map(f::Function, walker::GitRevWalker; oid::GitHash=GitHash(), range::AbstractString="", by::Cint=Consts.SORT_NONE, rev::Bool=false)
```

En utilisant le [`GitRevWalker`](@ref) `walker` pour "parcourir" chaque commit dans l'historique du dépôt, appliquez `f` à chaque commit dans le parcours. Les arguments clés sont :     * `oid` : Le [`GitHash`](@ref) du commit à partir duquel commencer le parcours. La valeur par défaut est d'utiliser       [`push_head!`](@ref) et donc le commit HEAD et tous ses ancêtres.     * `range` : Une plage de `GitHash`s au format `oid1..oid2`. `f` sera       appliqué à tous les commits entre les deux.     * `by` : La méthode de tri. La valeur par défaut est de ne pas trier. D'autres options consistent à trier par       topologie (`LibGit2.Consts.SORT_TOPOLOGICAL`), à trier dans le temps       (`LibGit2.Consts.SORT_TIME`, le plus ancien en premier) ou à trier à l'envers dans le temps       (`LibGit2.Consts.SORT_REVERSE`, le plus récent en premier).     * `rev` : Indique si l'ordre trié doit être inversé (par exemple, si le tri topologique est utilisé).

# Exemples

```julia
oids = LibGit2.with(LibGit2.GitRevWalker(repo)) do walker
    LibGit2.map((oid, repo)->string(oid), walker, by=LibGit2.Consts.SORT_TIME)
end
```

Ici, `LibGit2.map` visite chaque commit en utilisant le `GitRevWalker` et trouve son `GitHash`.
