```
watch_folder(path::AbstractString, timeout_s::Real=-1)
```

Surveille un fichier ou un répertoire `path` pour des changements jusqu'à ce qu'un changement se soit produit ou que `timeout_s` secondes se soient écoulées. Cette fonction ne scrute pas le système de fichiers et utilise plutôt des fonctionnalités spécifiques à la plateforme pour recevoir des notifications du système d'exploitation (par exemple, via inotify sur Linux). Voir la documentation NodeJS liée ci-dessous pour plus de détails.

Cela continuera à suivre les changements pour `path` en arrière-plan jusqu'à ce que `unwatch_folder` soit appelé sur le même `path`.

La valeur retournée est une paire où le premier champ est le nom du fichier modifié (si disponible) et le deuxième champ est un objet avec des champs booléens `renamed`, `changed` et `timedout`, indiquant l'événement.

Ce comportement de cette fonction varie légèrement selon les plateformes. Voir [https://nodejs.org/api/fs.html#fs_caveats](https://nodejs.org/api/fs.html#fs_caveats) pour des informations plus détaillées.
