```
LibGit2.gitdir(repo::GitRepo)
```

Retourne l'emplacement des fichiers "git" de `repo` :

  * pour les dépôts normaux, c'est l'emplacement du dossier `.git`.
  * pour les dépôts nus, c'est l'emplacement du dépôt lui-même.

Voir aussi [`workdir`](@ref), [`path`](@ref).
