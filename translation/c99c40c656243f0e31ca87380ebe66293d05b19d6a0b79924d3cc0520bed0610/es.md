```
wait([x])
```

Bloquea la tarea actual hasta que ocurra algún evento, dependiendo del tipo del argumento:

  * [`Channel`](@ref): Espera a que se agregue un valor al canal.
  * [`Condition`](@ref): Espera a que se llame a [`notify`](@ref) en una condición y devuelve el parámetro `val` pasado a `notify`. Esperar en una condición permite además pasar `first=true`, lo que resulta en que el que espera se coloque *primero* en la fila para despertarse en `notify` en lugar del comportamiento habitual de primero en entrar, primero en salir.
  * `Process`: Espera a que un proceso o cadena de procesos termine. El campo `exitcode` de un proceso se puede usar para determinar el éxito o el fracaso.
  * [`Task`](@ref): Espera a que una `Task` termine. Si la tarea falla con una excepción, se lanza una `TaskFailedException` (que envuelve la tarea fallida).
  * [`RawFD`](@ref): Espera cambios en un descriptor de archivo (ver el paquete `FileWatching`).

Si no se pasa ningún argumento, la tarea se bloquea por un período indefinido. Una tarea solo se puede reiniciar mediante una llamada explícita a [`schedule`](@ref) o [`yieldto`](@ref).

A menudo, `wait` se llama dentro de un bucle `while` para asegurar que se cumpla una condición esperada antes de continuar.
