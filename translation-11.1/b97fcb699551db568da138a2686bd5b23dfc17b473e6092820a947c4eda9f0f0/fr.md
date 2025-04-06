```
open(filename::AbstractString; lock = true, keywords...) -> IOStream
```

Ouvrir un fichier dans un mode spécifié par cinq arguments de mot-clé booléens :

| Mot-clé    | Description            | Par défaut                            |
|:---------- |:---------------------- |:------------------------------------- |
| `read`     | ouvrir pour lecture    | `!write`                              |
| `write`    | ouvrir pour écriture   | `truncate \| append`                  |
| `create`   | créer si non existant  | `!read & write \| truncate \| append` |
| `truncate` | tronquer à zéro taille | `!read & write`                       |
| `append`   | se déplacer à la fin   | `false`                               |

La valeur par défaut lorsque aucun mot-clé n'est passé est d'ouvrir les fichiers uniquement pour la lecture. Renvoie un flux pour accéder au fichier ouvert.

L'argument de mot-clé `lock` contrôle si les opérations seront verrouillées pour un accès multi-threadé sécurisé.

!!! compat "Julia 1.5"
    L'argument `lock` est disponible depuis Julia 1.5.

