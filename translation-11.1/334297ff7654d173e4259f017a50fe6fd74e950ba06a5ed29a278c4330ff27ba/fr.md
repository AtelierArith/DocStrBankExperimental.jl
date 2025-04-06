```
LibGit2.path(repo::GitRepo)
```

Retourne le chemin de base du fichier du dépôt `repo`.

  * pour les dépôts normaux, cela sera généralement le répertoire parent du répertoire ".git" (note : cela peut être différent du répertoire de travail, voir `workdir` pour plus de détails).
  * pour les dépôts nus, c'est l'emplacement des fichiers "git".

Voir aussi [`gitdir`](@ref), [`workdir`](@ref).
