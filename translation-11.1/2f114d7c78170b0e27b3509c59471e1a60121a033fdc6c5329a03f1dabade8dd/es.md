```
islocked(lock) -> Estado (Booleano)
```

Verifica si el `lock` está sostenido por alguna tarea/hilo. Esta función por sí sola no debe ser utilizada para sincronización. Sin embargo, `islocked` combinado con [`trylock`](@ref) puede ser utilizado para escribir los algoritmos de prueba-y-prueba-y-establecer o retroceso exponencial *si es soportado por el `typeof(lock)`* (lee su documentación).

# Ayuda extendida

Por ejemplo, un retroceso exponencial puede ser implementado de la siguiente manera si la implementación del `lock` satisface las propiedades documentadas a continuación.

```julia
nspins = 0
while true
    while islocked(lock)
        GC.safepoint()
        nspins += 1
        nspins > LIMIT && error("timeout")
    end
    trylock(lock) && break
    backoff()
end
```

## Implementación

Se aconseja a una implementación de lock definir `islocked` con las siguientes propiedades y anotarlo en su docstring.

  * `islocked(lock)` es libre de condiciones de carrera.
  * Si `islocked(lock)` devuelve `false`, una invocación inmediata de `trylock(lock)` debe tener éxito (devolver `true`) si no hay interferencia de otras tareas.
