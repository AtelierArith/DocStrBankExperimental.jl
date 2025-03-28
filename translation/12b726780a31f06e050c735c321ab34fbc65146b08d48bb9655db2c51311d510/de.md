```
indexpids(S::SharedArray)
```

Gibt den aktuellen Index des Arbeiters in der Liste der Arbeiter zurück, die das `SharedArray` zuordnen (d.h. in derselben Liste, die von `procs(S)` zurückgegeben wird), oder 0, wenn das `SharedArray` nicht lokal zugeordnet ist.
