```
stale_pidfile(path::String, stale_age::Real, refresh::Real) :: Bool
```

Fonction d'assistance pour `open_exclusive` pour décider si un fichier pid est obsolète.
