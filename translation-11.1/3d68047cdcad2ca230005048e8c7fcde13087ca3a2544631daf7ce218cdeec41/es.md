```
ReentrantLock()
```

Crea un candado reentrante para sincronizar [`Task`](@ref)s. La misma tarea puede adquirir el candado tantas veces como sea necesario (esto es lo que significa la parte "Reentrante" del nombre). Cada [`lock`](@ref) debe coincidir con un [`unlock`](@ref).

Llamar a `lock` también inhibirá la ejecución de finalizadores en ese hilo hasta el correspondiente `unlock`. El uso del patrón de bloqueo estándar ilustrado a continuación debería ser naturalmente compatible, pero ten cuidado de invertir el orden de try/lock o de omitir completamente el bloque try (por ejemplo, intentar devolver con el candado aún sostenido):

Esto proporciona un orden de memoria de adquisición/liberación en las llamadas de lock/unlock.

```
lock(l)
try
    <trabajo atómico>
finally
    unlock(l)
end
```

Si [`!islocked(lck::ReentrantLock)`](@ref islocked) se cumple, [`trylock(lck)`](@ref trylock) tendrá éxito a menos que haya otras tareas intentando mantener el candado "al mismo tiempo."
