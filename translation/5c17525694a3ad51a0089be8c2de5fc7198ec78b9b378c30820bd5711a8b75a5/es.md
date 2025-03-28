```
close(c::Channel[, excp::Exception])
```

Cierra un canal. Se lanza una excepción (opcionalmente dada por `excp`) por:

  * [`put!`](@ref) en un canal cerrado.
  * [`take!`](@ref) y [`fetch`](@ref) en un canal cerrado y vacío.
