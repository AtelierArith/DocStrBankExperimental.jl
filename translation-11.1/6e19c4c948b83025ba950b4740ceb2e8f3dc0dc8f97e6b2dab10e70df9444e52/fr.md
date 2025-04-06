```
LibGit2.CloneOptions
```

Correspond à la structure [`git_clone_options`](https://libgit2.org/libgit2/#HEAD/type/git_clone_options).

Les champs représentent :

  * `version` : version de la structure en cours d'utilisation, au cas où cela changerait plus tard. Pour l'instant, toujours `1`.
  * `checkout_opts` : Les options pour effectuer le checkout du distant dans le cadre du clonage.
  * `fetch_opts` : Les options pour effectuer le fetch pré-checkout du distant dans le cadre du clonage.
  * `bare` : Si `0`, cloner le dépôt distant complet. Si non nul, effectuer un clonage nu, dans lequel il n'y a pas de copie locale des fichiers sources dans le dépôt et les [`gitdir`](@ref) et [`workdir`](@ref) sont les mêmes.
  * `localclone` : Indicateur pour savoir s'il faut cloner une base de données d'objets locale ou faire un fetch. La valeur par défaut est de laisser git décider. Il n'utilisera pas le transport conscient de git pour un clonage local, mais l'utilisera pour les URL qui commencent par `file://`.
  * `checkout_branch` : Le nom de la branche à vérifier. Si une chaîne vide, la branche par défaut du distant sera vérifiée.
  * `repository_cb` : Un rappel optionnel qui sera utilisé pour créer le *nouveau* dépôt dans lequel le clonage est effectué.
  * `repository_cb_payload` : La charge utile pour le rappel du dépôt.
  * `remote_cb` : Un rappel optionnel utilisé pour créer le [`GitRemote`](@ref) avant de faire le clonage à partir de celui-ci.
  * `remote_cb_payload` : La charge utile pour le rappel distant.
