```
mkpidlock([f::Function], at::String, [pid::Cint]; kwopts...)
mkpidlock(at::String, proc::Process; kwopts...)
```

Crea un bloqueo de pidfile para la ruta "at" para el proceso actual o el proceso identificado por pid o proc. Puede tomar una función para ejecutar una vez bloqueado, para su uso en bloques `do`, después de lo cual el bloqueo se cerrará automáticamente. Si el bloqueo falla y `wait` es falso, se lanzará un error.

El bloqueo se liberará ya sea por `close`, un `finalizer`, o poco después de que `proc` salga. Asegúrate de que el valor de retorno esté vivo hasta el final de la sección crítica de tu programa, para que el `finalizer` no lo recupere demasiado pronto.

Argumentos opcionales:

  * `mode`: modo de acceso al archivo (modificado por la máscara de usuario del proceso). Por defecto es legible por todos.
  * `poll_interval`: Especifica el tiempo máximo entre intentos (si `watch_file` no funciona)
  * `stale_age`: Elimina un pidfile existente (ignorando el bloqueo) si es más antiguo que esta cantidad de segundos, basado en su mtime. El archivo no se eliminará hasta 5x más que esto si el pid en el archivo parece que puede ser válido. O 25x más si `refresh` se anula a 0 para deshabilitar la actualización del bloqueo. Por defecto, esto está deshabilitado (`stale_age` = 0), pero un valor típico recomendado sería alrededor de 3-5x un tiempo de finalización normal estimado.
  * `refresh`: Mantiene un bloqueo de volverse obsoleto actualizando el mtime cada intervalo de tiempo que pasa. Por defecto, esto se establece en `stale_age/2`, que es el valor recomendado.
  * `wait`: Si es verdadero, bloquea hasta que obtengamos el bloqueo; si es falso, lanza un error si el bloqueo falla.
