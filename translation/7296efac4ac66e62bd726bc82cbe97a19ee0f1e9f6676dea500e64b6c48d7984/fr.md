```
LibGit2.DiffOptionsStruct
```

Correspond à la structure [`git_diff_options`](https://libgit2.org/libgit2/#HEAD/type/git_diff_options).

Les champs représentent :

  * `version` : version de la structure en cours d'utilisation, au cas où cela changerait plus tard. Pour l'instant, toujours `1`.
  * `flags` : drapeaux contrôlant quels fichiers apparaîtront dans le diff. Par défaut, `DIFF_NORMAL`.
  * `ignore_submodules` : indique s'il faut examiner les fichiers dans les sous-modules ou non. Par défaut, `SUBMODULE_IGNORE_UNSPECIFIED`, ce qui signifie que la configuration du sous-module contrôlera s'il apparaît dans le diff ou non.
  * `pathspec` : chemin vers les fichiers à inclure dans le diff. Par défaut, tous les fichiers du dépôt sont utilisés.
  * `notify_cb` : rappel optionnel qui notifiera l'utilisateur des changements dans le diff à mesure que des deltas de fichiers y sont ajoutés.
  * `progress_cb` : rappel optionnel qui affichera la progression du diff. Pertinent uniquement sur les versions de libgit2 au moins aussi récentes que 0.24.0.
  * `payload` : la charge utile à passer à `notify_cb` et `progress_cb`.
  * `context_lines` : le nombre de lignes *inchangées* utilisées pour définir les bords d'un hunk. C'est également le nombre de lignes qui seront affichées avant/après un hunk pour fournir un contexte. Par défaut, 3.
  * `interhunk_lines` : le nombre maximum de lignes *inchangées* *entre* deux hunks séparés autorisées avant que les hunks ne soient combinés. Par défaut, 0.
  * `id_abbrev` : définit la longueur de l'abrégé [`GitHash`](@ref) à imprimer. Par défaut, `7`.
  * `max_size` : la taille maximale d'un fichier blob. Au-dessus de cette taille, il sera traité comme un blob binaire. La valeur par défaut est 512 Mo.
  * `old_prefix` : le répertoire de fichiers virtuel dans lequel placer les anciens fichiers d'un côté du diff. Par défaut, `"a"`.
  * `new_prefix` : le répertoire de fichiers virtuel dans lequel placer les nouveaux fichiers d'un côté du diff. Par défaut, `"b"`.
