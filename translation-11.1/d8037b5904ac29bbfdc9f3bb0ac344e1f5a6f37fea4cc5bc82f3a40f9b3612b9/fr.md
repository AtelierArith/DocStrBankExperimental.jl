```
LibGit2.DiffDelta
```

Description des changements apportés à une entrée. Correspond à la structure [`git_diff_delta`](https://libgit2.org/libgit2/#HEAD/type/git_diff_delta).

Les champs représentent :

  * `status` : L'un des `Consts.DELTA_STATUS`, indiquant si le fichier a été ajouté/modifié/supprimé.
  * `flags` : Drapeaux pour le delta et les objets de chaque côté. Détermine s'il faut traiter le(s) fichier(s) comme binaire/texte, s'ils existent de chaque côté du diff, et si les identifiants d'objet sont connus pour être corrects.
  * `similarity` : Utilisé pour indiquer si un fichier a été renommé ou copié.
  * `nfiles` : Le nombre de fichiers dans le delta (par exemple, si le delta a été exécuté sur un identifiant de commit de sous-module, il peut contenir plus d'un fichier).
  * `old_file` : Un [`DiffFile`](@ref) contenant des informations sur le(s) fichier(s) avant les changements.
  * `new_file` : Un [`DiffFile`](@ref) contenant des informations sur le(s) fichier(s) après les changements.
