```
Threads.Condition([lock])
```

Una versión segura para hilos de [`Base.Condition`](@ref).

Para llamar a [`wait`](@ref) o [`notify`](@ref) en un `Threads.Condition`, primero debes llamar a [`lock`](@ref) en él. Cuando se llama a `wait`, el bloqueo se libera atómicamente durante el bloqueo y se volverá a adquirir antes de que `wait` regrese. Por lo tanto, el uso idiomático de un `Threads.Condition` `c` se ve como sigue:

```
lock(c)
try
    while !thing_we_are_waiting_for
        wait(c)
    end
finally
    unlock(c)
end
```

!!! compat "Julia 1.2"
    Esta funcionalidad requiere al menos Julia 1.2.

