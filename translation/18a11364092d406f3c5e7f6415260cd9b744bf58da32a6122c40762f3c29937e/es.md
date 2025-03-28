```
systemsleep(s::Real)
```

Suspende la ejecución durante `s` segundos. Esta función no cede al programador de Julia y, por lo tanto, bloquea el hilo de Julia en el que se está ejecutando durante la duración del tiempo de suspensión.

Véase también [`sleep`](@ref).
