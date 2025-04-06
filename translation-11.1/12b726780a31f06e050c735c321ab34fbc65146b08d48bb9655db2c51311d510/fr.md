```
indexpids(S::SharedArray)
```

Renvoie l'index du travailleur actuel dans la liste des travailleurs mappant le `SharedArray` (c'est-à-dire dans la même liste retournée par `procs(S)`), ou 0 si le `SharedArray` n'est pas mappé localement.
