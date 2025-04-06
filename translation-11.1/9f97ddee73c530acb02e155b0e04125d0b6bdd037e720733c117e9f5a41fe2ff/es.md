```
trylock(lock) -> Éxito (Booleano)
```

Adquiere el bloqueo si está disponible y devuelve `true` si tiene éxito. Si el bloqueo ya está bloqueado por otra tarea/hilo, devuelve `false`.

Cada `trylock` exitoso debe ser emparejado con un [`unlock`](@ref).

La función `trylock` combinada con [`islocked`](@ref) se puede usar para escribir los algoritmos de prueba-y-prueba-y-establecer o retroceso exponencial *si es compatible con el `typeof(lock)`* (lee su documentación).
