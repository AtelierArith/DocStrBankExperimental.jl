```
put!(rr::RemoteChannel, args...)
```

Almacena un conjunto de valores en el [`RemoteChannel`](@ref). Si el canal está lleno, bloquea hasta que haya espacio disponible. Devuelve el primer argumento.
