```
tryopen_exclusive(path::String, mode::Integer = 0o444) :: Union{Void, File}
```

Intenta crear un nuevo archivo para acceso exclusivo de lectura-escritura, devuelve nada si ya existe.
