```
GitRevWalker(repo::GitRepo)
```

Un `GitRevWalker` *parcourt* les *révisions* (c'est-à-dire les commits) d'un dépôt git `repo`. C'est une collection des commits dans le dépôt, et il prend en charge l'itération et les appels à [`LibGit2.map`](@ref) et [`LibGit2.count`](@ref) (par exemple, `LibGit2.count` pourrait être utilisé pour déterminer quel pourcentage de commits dans un dépôt a été réalisé par un certain auteur).

```julia
cnt = LibGit2.with(LibGit2.GitRevWalker(repo)) do walker
    LibGit2.count((oid,repo)->(oid == commit_oid1), walker, oid=commit_oid1, by=LibGit2.Consts.SORT_TIME)
end
```

Ici, `LibGit2.count` trouve le nombre de commits le long de la marche avec un certain `GitHash`. Puisque le `GitHash` est unique à un commit, `cnt` sera `1`.
