```
LibGit2.MergeOptions
```

Correspond à la structure [`git_merge_options`](https://libgit2.org/libgit2/#HEAD/type/git_merge_options).

Les champs représentent :

  * `version` : version de la structure en cours d'utilisation, au cas où cela changerait plus tard. Pour l'instant, toujours `1`.
  * `flags` : un `enum` pour les drapeaux décrivant le comportement de fusion. Défini dans [`git_merge_flag_t`](https://github.com/libgit2/libgit2/blob/HEAD/include/git2/merge.h#L95). L'énumération Julia correspondante est `GIT_MERGE` et a les valeurs :

      * `MERGE_FIND_RENAMES` : détecter si un fichier a été renommé entre l'ancêtre commun et le côté "notre" ou "leur" de la fusion. Permet des fusions où un fichier a été renommé.
      * `MERGE_FAIL_ON_CONFLICT` : sortir immédiatement si un conflit est trouvé plutôt que d'essayer de le résoudre.
      * `MERGE_SKIP_REUC` : ne pas écrire l'extension REUC sur l'index résultant de la fusion.
      * `MERGE_NO_RECURSIVE` : si les commits à fusionner ont plusieurs bases de fusion, utiliser la première, plutôt que d'essayer de fusionner les bases de manière récursive.
  * `rename_threshold` : à quel point deux fichiers doivent être similaires pour considérer l'un comme un renommage de l'autre. C'est un entier qui fixe le pourcentage de similarité. La valeur par défaut est 50.
  * `target_limit` : le nombre maximum de fichiers à comparer pour rechercher des renommages. La valeur par défaut est 200.
  * `metric` : fonction personnalisée optionnelle à utiliser pour déterminer la similarité entre deux fichiers pour la détection de renommage.
  * `recursion_limit` : la limite supérieure sur le nombre de fusions d'ancêtres communs à effectuer pour essayer de construire une nouvelle base de fusion virtuelle pour la fusion. La valeur par défaut est sans limite. Ce champ n'est présent que dans les versions de libgit2 plus récentes que 0.24.0.
  * `default_driver` : le pilote de fusion à utiliser si les deux côtés ont changé. Ce champ n'est présent que dans les versions de libgit2 plus récentes que 0.25.0.
  * `file_favor` : comment gérer les contenus de fichiers conflictuels pour le pilote `text`.

      * `MERGE_FILE_FAVOR_NORMAL` : si les deux côtés de la fusion ont des modifications dans une section, notez le conflit dans l'index que `git checkout` utilisera pour créer un fichier de fusion, que l'utilisateur pourra ensuite référencer pour résoudre les conflits. C'est la valeur par défaut.
      * `MERGE_FILE_FAVOR_OURS` : si les deux côtés de la fusion ont des modifications dans une section, utilisez la version du côté "notre" de la fusion dans l'index.
      * `MERGE_FILE_FAVOR_THEIRS` : si les deux côtés de la fusion ont des modifications dans une section, utilisez la version du côté "leur" de la fusion dans l'index.
      * `MERGE_FILE_FAVOR_UNION` : si les deux côtés de la fusion ont des modifications dans une section, incluez chaque ligne unique des deux côtés dans le fichier qui est mis dans l'index.
  * `file_flags` : directives pour fusionner des fichiers.
