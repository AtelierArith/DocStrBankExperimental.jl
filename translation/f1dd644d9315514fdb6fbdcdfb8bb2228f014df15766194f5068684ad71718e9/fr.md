```
LibGit2.StatusOptions
```

Options pour contrôler comment `git_status_foreach_ext()` émettra des rappels. Correspond à la structure [`git_status_opt_t`](https://libgit2.org/libgit2/#HEAD/type/git_status_opt_t).

Les champs représentent :

  * `version` : version de la structure en cours d'utilisation, au cas où cela changerait plus tard. Pour l'instant, toujours `1`.
  * `show` : un indicateur pour quels fichiers examiner et dans quel ordre. La valeur par défaut est `Consts.STATUS_SHOW_INDEX_AND_WORKDIR`.
  * `flags` : indicateurs pour contrôler les rappels utilisés dans un appel de statut.
  * `pathspec` : un tableau de chemins à utiliser pour le filtrage des chemins. Le comportement du filtrage des chemins variera en fonction des valeurs de `show` et `flags`.
  * Le `baseline` est l'arbre à utiliser pour la comparaison avec le répertoire de travail et l'index ; par défaut, c'est HEAD.
