```
LibGit2.BlameOptions
```

Correspond à la structure [`git_blame_options`](https://libgit2.org/libgit2/#HEAD/type/git_blame_options).

Les champs représentent :

  * `version` : version de la structure en cours d'utilisation, au cas où cela changerait plus tard. Pour l'instant, toujours `1`.
  * `flags` : l'un de `Consts.BLAME_NORMAL` ou `Consts.BLAME_FIRST_PARENT` (les autres drapeaux de blame ne sont pas encore implémentés par libgit2).
  * `min_match_characters` : le nombre minimum de caractères *alphanumériques* qui doivent changer dans un commit pour que le changement soit associé à ce commit. La valeur par défaut est 20. N'entre en vigueur que si l'un des drapeaux `Consts.BLAME_*_COPIES` est utilisé, ce que libgit2 n'implémente pas encore.
  * `newest_commit` : le [`GitHash`](@ref) du commit le plus récent à partir duquel examiner les changements.
  * `oldest_commit` : le [`GitHash`](@ref) du commit le plus ancien à partir duquel examiner les changements.
  * `min_line` : la première ligne du fichier à partir de laquelle commencer à blâmer. La valeur par défaut est `1`.
  * `max_line` : la dernière ligne du fichier à laquelle blâmer. La valeur par défaut est `0`, ce qui signifie la dernière ligne du fichier.
