```
open_exclusive(path::String; mode, poll_interval, wait, stale_age, refresh) :: File
```

Crea un nuevo archivo para acceso exclusivo de lectura-escritura por asesoría. Si `wait` es `false`, entonces genera un error si los archivos de bloqueo existen; de lo contrario, bloquea hasta que obtengamos el bloqueo.

Para una descripción de los argumentos de palabra clave, consulta [`mkpidlock`](@ref).
