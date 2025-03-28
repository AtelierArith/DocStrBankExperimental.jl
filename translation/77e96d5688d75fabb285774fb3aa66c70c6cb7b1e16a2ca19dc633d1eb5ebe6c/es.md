```
@async
```

Envuelve una expresión en una [`Task`](@ref) y añádela a la cola del programador de la máquina local.

Los valores se pueden interpolar en `@async` a través de `$`, que copia el valor directamente en el cierre subyacente construido. Esto te permite insertar el *valor* de una variable, aislando el código asíncrono de los cambios en el valor de la variable en la tarea actual.

!!! warning
    Se recomienda encarecidamente favorecer `Threads.@spawn` sobre `@async` siempre **incluso cuando no se requiera paralelismo**, especialmente en bibliotecas distribuidas públicamente. Esto se debe a que el uso de `@async` desactiva la migración de la tarea *padre* a través de hilos de trabajo en la implementación actual de Julia. Por lo tanto, el uso aparentemente inocente de `@async` en una función de biblioteca puede tener un gran impacto en el rendimiento de partes muy diferentes de las aplicaciones de los usuarios.


!!! compat "Julia 1.4"
    La interpolación de valores a través de `$` está disponible desde Julia 1.4.

