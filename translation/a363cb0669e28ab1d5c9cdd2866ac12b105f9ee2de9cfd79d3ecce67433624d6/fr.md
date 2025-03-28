```
LibGit2.GitStatus(repo::GitRepo; status_opts=StatusOptions())
```

Collecte des informations sur l'état de chaque fichier dans le dépôt git `repo` (par exemple, si le fichier est modifié, mis en scène, etc.). `status_opts` peut être utilisé pour définir diverses options, par exemple, s'il faut ou non examiner les fichiers non suivis ou s'il faut inclure ou non les sous-modules. Voir [`StatusOptions`](@ref) pour plus d'informations.
