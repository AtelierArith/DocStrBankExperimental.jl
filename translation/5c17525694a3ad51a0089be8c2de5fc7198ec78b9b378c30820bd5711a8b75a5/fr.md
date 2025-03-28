```
close(c::Channel[, excp::Exception])
```

Ferme un canal. Une exception (facultativement donnée par `excp`) est levée par :

  * [`put!`](@ref) sur un canal fermé.
  * [`take!`](@ref) et [`fetch`](@ref) sur un canal fermé et vide.
