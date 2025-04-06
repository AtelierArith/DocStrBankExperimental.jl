```
LibGit2.workdir(repo::GitRepo)
```

Renvoie l'emplacement du répertoire de travail de `repo`. Cela générera une erreur pour les dépôts nus.

!!! note
    Cela sera généralement le répertoire parent de `gitdir(repo)`, mais peut être différent dans certains cas : par exemple, si la variable de configuration `core.worktree` ou la variable d'environnement `GIT_WORK_TREE` est définie.


Voir aussi [`gitdir`](@ref), [`path`](@ref).
