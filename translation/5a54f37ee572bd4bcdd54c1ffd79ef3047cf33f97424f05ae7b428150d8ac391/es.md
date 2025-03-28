```
GC.gc([full=true])
```

Realiza la recolección de basura. El argumento `full` determina el tipo de recolección: una recolección completa (por defecto) recorre todos los objetos vivos (es decir, marca completa) y debería recuperar memoria de todos los objetos inalcanzables. Una recolección incremental solo recupera memoria de objetos jóvenes que no son alcanzables.

El GC puede decidir realizar una recolección completa incluso si se solicitó una recolección incremental.

!!! warning
    El uso excesivo probablemente conducirá a un rendimiento deficiente.

