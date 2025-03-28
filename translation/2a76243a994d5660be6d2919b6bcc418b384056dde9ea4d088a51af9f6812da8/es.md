```
setrounding(f::Function, T, mode)
```

Cambia el modo de redondeo del tipo de punto flotante `T` durante la duración de `f`. Es lógicamente equivalente a:

```
old = rounding(T)
setrounding(T, mode)
f()
setrounding(T, old)
```

Consulta [`RoundingMode`](@ref) para los modos de redondeo disponibles.
