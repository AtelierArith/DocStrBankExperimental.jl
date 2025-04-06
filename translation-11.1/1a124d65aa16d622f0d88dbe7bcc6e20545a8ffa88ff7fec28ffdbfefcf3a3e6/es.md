```
reset(s::IO)
```

Restablece un flujo `s` a una posición marcada previamente y elimina la marca. Devuelve la posición marcada previamente. Lanza un error si el flujo no está marcado.

Véase también [`mark`](@ref), [`unmark`](@ref), [`ismarked`](@ref).
