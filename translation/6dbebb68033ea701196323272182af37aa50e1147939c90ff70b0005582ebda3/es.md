```
lock(f::Function, lock)
```

Adquiere el `lock`, ejecuta `f` con el `lock` mantenido, y libera el `lock` cuando `f` retorna. Si el lock ya está bloqueado por otra tarea/hilo, espera a que esté disponible.

Cuando esta función retorna, el `lock` ha sido liberado, por lo que el llamador no debe intentar `unlock`earlo.

Ver también: [`@lock`](@ref).

!!! compat "Julia 1.7"
    Usar un [`Channel`](@ref) como segundo argumento requiere Julia 1.7 o posterior.

