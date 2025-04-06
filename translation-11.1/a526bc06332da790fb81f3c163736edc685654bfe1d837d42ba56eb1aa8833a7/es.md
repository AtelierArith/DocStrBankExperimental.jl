```
Base.touch(::Pidfile.LockMonitor)
```

Actualiza el `mtime` en el bloqueo, para indicar que sigue siendo reciente.

Consulta también la palabra clave `refresh` en el constructor [`mkpidlock`](@ref).
