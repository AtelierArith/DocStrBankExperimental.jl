```
watch_file(path::AbstractString, timeout_s::Real=-1)
```

Surveillez le fichier ou le répertoire `path` pour des changements jusqu'à ce qu'un changement se produise ou que `timeout_s` secondes se soient écoulées. Cette fonction ne scrute pas le système de fichiers et utilise plutôt des fonctionnalités spécifiques à la plateforme pour recevoir des notifications du système d'exploitation (par exemple, via inotify sur Linux). Consultez la documentation NodeJS liée ci-dessous pour plus de détails.

La valeur retournée est un objet avec des champs booléens `renamed`, `changed` et `timedout`, donnant le résultat de la surveillance du fichier.

Ce comportement de cette fonction varie légèrement selon les plateformes. Voir [https://nodejs.org/api/fs.html#fs_caveats](https://nodejs.org/api/fs.html#fs_caveats) pour des informations plus détaillées.
