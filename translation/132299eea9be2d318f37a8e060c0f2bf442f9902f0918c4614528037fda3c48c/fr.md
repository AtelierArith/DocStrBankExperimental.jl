```
LibGit2.StatusEntry
```

Fournit les différences entre le fichier tel qu'il existe dans HEAD et l'index, et fournit les différences entre l'index et le répertoire de travail. Correspond à la structure `git_status_entry`.

Les champs représentent :

  * `status` : contient les indicateurs de statut pour le fichier, indiquant s'il est à jour ou s'il a été modifié d'une manière ou d'une autre dans l'index ou l'arbre de travail.
  * `head_to_index` : un pointeur vers un [`DiffDelta`](@ref) qui encapsule la ou les différences entre le fichier tel qu'il existe dans HEAD et dans l'index.
  * `index_to_workdir` : un pointeur vers un `DiffDelta` qui encapsule la ou les différences entre le fichier tel qu'il existe dans l'index et dans le [`workdir`](@ref).
