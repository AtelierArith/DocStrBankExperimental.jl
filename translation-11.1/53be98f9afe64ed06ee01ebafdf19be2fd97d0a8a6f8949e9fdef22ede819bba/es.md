```
reset(::Event)
```

Restablece un [`Event`](@ref) a un estado no establecido. Luego, cualquier llamada futura a `wait` bloqueará hasta que se llame a [`notify`](@ref) nuevamente.
