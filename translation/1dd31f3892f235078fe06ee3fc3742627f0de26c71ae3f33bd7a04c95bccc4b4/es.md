```
worker_id_from_socket(s) -> pid
```

Una API de bajo nivel que, dado un `IO` conexión o un `Worker`, devuelve el `pid` del trabajador al que está conectado. Esto es útil al escribir métodos personalizados [`serialize`](@ref) para un tipo, que optimizan los datos escritos dependiendo del id del proceso receptor.
