```
lock(lock)
```

Adquiere el `lock` cuando esté disponible. Si el lock ya está bloqueado por otra tarea/hilo, espera a que esté disponible.

Cada `lock` debe ser emparejado con un [`unlock`](@ref).
