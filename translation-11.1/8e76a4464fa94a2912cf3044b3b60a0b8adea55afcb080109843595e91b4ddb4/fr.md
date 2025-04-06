```
LibGit2.DiffFile
```

Description d'un côté d'un delta. Correspond à la structure [`git_diff_file`](https://libgit2.org/libgit2/#HEAD/type/git_diff_file).

Les champs représentent :

  * `id` : le [`GitHash`](@ref) de l'élément dans le diff. Si l'élément est vide de ce côté du diff (par exemple, si le diff concerne la suppression d'un fichier), cela sera `GitHash(0)`.
  * `path` : un chemin terminé par `NULL` vers l'élément relatif au répertoire de travail du dépôt.
  * `size` : la taille de l'élément en octets.
  * `flags` : une combinaison des drapeaux [`git_diff_flag_t`](https://libgit2.org/libgit2/#HEAD/type/git_diff_flag_t). Le `i`-ème bit de cet entier définit le `i`-ème drapeau.
  * `mode` : le mode [`stat`](@ref) pour l'élément.
  * `id_abbrev` : présent uniquement dans les versions de LibGit2 supérieures ou égales à `0.25.0`. La longueur du champ `id` lorsqu'il est converti en utilisant [`string`](@ref). Généralement égal à `OID_HEXSZ` (40).
