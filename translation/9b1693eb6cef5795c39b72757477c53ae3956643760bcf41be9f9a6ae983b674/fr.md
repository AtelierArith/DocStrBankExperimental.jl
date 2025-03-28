```
mktemp(parent=tempdir(); cleanup=true) -> (path, io)
```

Retourne `(path, io)`, où `path` est le chemin d'un nouveau fichier temporaire dans `parent` et `io` est un objet de fichier ouvert pour ce chemin. L'option `cleanup` contrôle si le fichier temporaire est automatiquement supprimé lorsque le processus se termine.

!!! compat "Julia 1.3"
    L'argument clé `cleanup` a été ajouté dans Julia 1.3. De manière connexe, à partir de 1.3, Julia supprimera les chemins temporaires créés par `mktemp` lorsque le processus Julia se termine, sauf si `cleanup` est explicitement défini sur `false`.

