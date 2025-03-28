```
channel_from_id(id) -> c
```

Una API de bajo nivel que devuelve el `AbstractChannel` de respaldo para un `id` devuelto por [`remoteref_id`](@ref). La llamada es válida solo en el nodo donde existe el canal de respaldo.
