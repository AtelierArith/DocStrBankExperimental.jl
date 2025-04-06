```
stale_pidfile(path::String, stale_age::Real, refresh::Real) :: Bool
```

Hilfsfunktion für `open_exclusive`, um zu entscheiden, ob eine pidfile veraltet ist.
