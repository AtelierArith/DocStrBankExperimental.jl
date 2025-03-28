```
stale_pidfile(path::String, stale_age::Real, refresh::Real) :: Bool
```

Función auxiliar para `open_exclusive` para decidir si un pidfile está obsoleto.
