```
atexit(f)
```

Registra una función de cero o un argumento `f()` que se llamará al salir del proceso. Los ganchos de `atexit()` se llaman en orden de último en entrar, primero en salir (LIFO) y se ejecutan antes de los finalizadores de objetos.

Si `f` tiene un método definido para un argumento entero, se llamará como `f(n::Int32)`, donde `n` es el código de salida actual; de lo contrario, se llamará como `f()`.

!!! compat "Julia 1.9"
    La forma de un argumento requiere Julia 1.9


Se permite que los ganchos de salida llamen a `exit(n)`, en cuyo caso Julia saldrá con el código de salida `n` (en lugar del código de salida original). Si más de un gancho de salida llama a `exit(n)`, entonces Julia saldrá con el código de salida correspondiente al último gancho de salida llamado que llama a `exit(n)`. (Debido a que los ganchos de salida se llaman en orden LIFO, "último llamado" es equivalente a "primero registrado".)

Nota: Una vez que se han llamado todos los ganchos de salida, no se pueden registrar más ganchos de salida, y cualquier llamada a `atexit(f)` después de que todos los ganchos se hayan completado lanzará una excepción. Esta situación puede ocurrir si estás registrando ganchos de salida desde Tareas en segundo plano que aún pueden estar ejecutándose de manera concurrente durante el apagado.
