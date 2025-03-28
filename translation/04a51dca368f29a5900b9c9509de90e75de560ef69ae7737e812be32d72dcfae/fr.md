```
open(command, stdio=devnull; write::Bool = false, read::Bool = !write)
```

Commencez à exécuter `command` de manière asynchrone et renvoyez un objet `process::IO`. Si `read` est vrai, alors les lectures du processus proviennent de la sortie standard du processus et `stdio` spécifie éventuellement le flux d'entrée standard du processus. Si `write` est vrai, alors les écritures vont au flux d'entrée standard du processus et `stdio` spécifie éventuellement le flux de sortie standard du processus. Le flux d'erreur standard du processus est connecté à l'`stderr` global actuel.
