```
LibGit2.FetchHead
```

Contient les informations sur HEAD lors d'un fetch, y compris le nom et l'URL de la branche à partir de laquelle il a été récupéré, l'oid de HEAD, et si le HEAD récupéré a été fusionné localement.

Les champs représentent :

  * `name` : Le nom dans la base de données de références locales du fetch head, par exemple,  `"refs/heads/master"`.
  * `url` : L'URL du fetch head.
  * `oid` : Le [`GitHash`](@ref) du sommet du fetch head.
  * `ismerge` : Indicateur booléen indiquant si les modifications à distance ont été fusionnées dans la copie locale ou non. Si `true`, la copie locale est à jour avec le fetch head distant.
