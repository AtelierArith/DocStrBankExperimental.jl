```
link_pipe!(pipe; reader_supports_async=false, writer_supports_async=false)
```

Initialisez `pipe` et reliez le point d'extrémité `in` au point d'extrémité `out`. Les arguments de mot-clé `reader_supports_async`/`writer_supports_async` correspondent à `OVERLAPPED` sur Windows et `O_NONBLOCK` sur les systèmes POSIX. Ils devraient être `true` à moins qu'ils ne soient utilisés par un programme externe (par exemple, la sortie d'une commande exécutée avec [`run`](@ref)).
