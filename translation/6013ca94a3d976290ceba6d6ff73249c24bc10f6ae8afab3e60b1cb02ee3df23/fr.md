```
add!(repo::GitRepo, files::AbstractString...; flags::Cuint = Consts.INDEX_ADD_DEFAULT)
add!(idx::GitIndex, files::AbstractString...; flags::Cuint = Consts.INDEX_ADD_DEFAULT)
```

Ajoutez tous les fichiers dont les chemins sont spécifiés par `files` à l'index `idx` (ou l'index du `repo`). Si le fichier existe déjà, l'entrée de l'index sera mise à jour. Si le fichier n'existe pas déjà, il sera nouvellement ajouté à l'index. `files` peut contenir des motifs glob qui seront développés et tous les fichiers correspondants seront ajoutés (à moins que `INDEX_ADD_DISABLE_PATHSPEC_MATCH` ne soit défini, voir ci-dessous). Si un fichier a été ignoré (dans `.gitignore` ou dans la configuration), il *ne sera pas* ajouté, *à moins* qu'il ne soit déjà suivi dans l'index, auquel cas il *sera* mis à jour. L'argument clé `flags` est un ensemble de bits qui contrôlent le comportement par rapport aux fichiers ignorés :

  * `Consts.INDEX_ADD_DEFAULT` - par défaut, décrit ci-dessus.
  * `Consts.INDEX_ADD_FORCE` - ignorer les règles d'ignorance existantes et forcer l'ajout du fichier à l'index même s'il est déjà ignoré.
  * `Consts.INDEX_ADD_CHECK_PATHSPEC` - ne peut pas être utilisé en même temps que `INDEX_ADD_FORCE`. Vérifiez que chaque fichier dans `files` qui existe sur le disque n'est pas dans la liste d'ignorance. Si l'un des fichiers *est* ignoré, la fonction renverra `EINVALIDSPEC`.
  * `Consts.INDEX_ADD_DISABLE_PATHSPEC_MATCH` - désactiver la correspondance glob, et n'ajouter que les fichiers à l'index qui correspondent exactement aux chemins spécifiés dans `files`.
