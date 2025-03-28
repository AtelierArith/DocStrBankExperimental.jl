```
message(c::GitCommit, raw::Bool=false)
```

Devuelve el mensaje de confirmación que describe los cambios realizados en la confirmación `c`. Si `raw` es `false`, devuelve un mensaje ligeramente "limpiado" (que tiene cualquier salto de línea inicial eliminado). Si `raw` es `true`, el mensaje no se elimina de ningún salto de línea.
