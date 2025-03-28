lock(f::Function, l::Lockable)

Adquiere el bloqueo asociado con `l`, ejecuta `f` con el bloqueo mantenido y libera el bloqueo cuando `f` regresa. `f` recibirá un argumento posicional: el valor envuelto por `l`. Si el bloqueo ya está bloqueado por otra tarea/hilo, espera a que esté disponible. Cuando esta función regresa, el `lock` ha sido liberado, por lo que el llamador no debe intentar `unlock`arlo.

!!! compat "Julia 1.11"
    Requiere al menos Julia 1.11.

