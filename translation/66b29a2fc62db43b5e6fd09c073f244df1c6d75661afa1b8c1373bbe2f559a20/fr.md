```
LibGit2.count(f::Function, walker::GitRevWalker; oid::GitHash=GitHash(), by::Cint=Consts.SORT_NONE, rev::Bool=false)
```

En utilisant le [`GitRevWalker`](@ref) `walker` pour "parcourir" chaque commit dans l'historique du dépôt, trouvez le nombre de commits qui retournent `true` lorsque `f` leur est appliqué. Les arguments clés sont :     * `oid` : Le [`GitHash`](@ref) du commit à partir duquel commencer le parcours. La valeur par défaut est d'utiliser       [`push_head!`](@ref) et donc le commit HEAD et tous ses ancêtres.     * `by` : La méthode de tri. La valeur par défaut est de ne pas trier. D'autres options sont de trier par       topologie (`LibGit2.Consts.SORT_TOPOLOGICAL`), de trier dans le temps       (`LibGit2.Consts.SORT_TIME`, le plus ancien en premier) ou de trier à rebours dans le temps       (`LibGit2.Consts.SORT_REVERSE`, le plus récent en premier).     * `rev` : Indique si l'ordre trié doit être inversé (par exemple, si un tri topologique est utilisé).

# Exemples

```julia
cnt = LibGit2.with(LibGit2.GitRevWalker(repo)) do walker
    LibGit2.count((oid, repo)->(oid == commit_oid1), walker, oid=commit_oid1, by=LibGit2.Consts.SORT_TIME)
end
```

`LibGit2.count` trouve le nombre de commits le long du parcours avec un certain `GitHash` `commit_oid1`, en commençant le parcours à partir de ce commit et en avançant dans le temps à partir de celui-ci. Puisque le `GitHash` est unique à un commit, `cnt` sera `1`.
