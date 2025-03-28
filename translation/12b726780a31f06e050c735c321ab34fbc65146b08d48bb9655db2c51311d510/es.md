```
indexpids(S::SharedArray)
```

Devuelve el índice del trabajador actual en la lista de trabajadores que mapean el `SharedArray` (es decir, en la misma lista devuelta por `procs(S)`), o 0 si el `SharedArray` no está mapeado localmente.
