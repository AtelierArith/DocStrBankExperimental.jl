```
wait([x])
```

Bloque la tâche actuelle jusqu'à ce qu'un événement se produise, en fonction du type de l'argument :

  * [`Channel`](@ref) : Attendre qu'une valeur soit ajoutée au canal.
  * [`Condition`](@ref) : Attendre [`notify`](@ref) sur une condition et retourner le paramètre `val` passé à `notify`. Attendre sur une condition permet également de passer `first=true`, ce qui fait que le wait est mis *en premier* dans la file d'attente pour se réveiller sur `notify` au lieu du comportement habituel premier arrivé, premier servi.
  * `Process` : Attendre qu'un processus ou une chaîne de processus se termine. Le champ `exitcode` d'un processus peut être utilisé pour déterminer le succès ou l'échec.
  * [`Task`](@ref) : Attendre qu'une `Task` se termine. Si la tâche échoue avec une exception, une `TaskFailedException` (qui enveloppe la tâche échouée) est levée.
  * [`RawFD`](@ref) : Attendre des changements sur un descripteur de fichier (voir le package `FileWatching`).

Si aucun argument n'est passé, la tâche se bloque pour une période indéfinie. Une tâche ne peut être redémarrée que par un appel explicite à [`schedule`](@ref) ou [`yieldto`](@ref).

Souvent, `wait` est appelé dans une boucle `while` pour s'assurer qu'une condition attendue est remplie avant de continuer.
