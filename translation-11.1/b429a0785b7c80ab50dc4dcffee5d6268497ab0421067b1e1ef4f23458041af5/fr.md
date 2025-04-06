```
CompositeException
```

Enveloppe un `Vector` d'exceptions levées par une [`Task`](@ref) (par exemple, générées par un travailleur distant via un canal ou une écriture I/O locale exécutée de manière asynchrone ou un travailleur distant sous `pmap`) avec des informations sur la série d'exceptions. Par exemple, si un groupe de travailleurs exécute plusieurs tâches, et que plusieurs travailleurs échouent, le `CompositeException` résultant contiendra un "paquet" d'informations de chaque travailleur indiquant où et pourquoi l(es) exception(s) s'est/sont produite(s).
