```
Profile.Allocs.print([io::IO = stdout,] [data::AllocResults = fetch()]; kwargs...)
```

Imprime los resultados de perfilado en `io` (por defecto, `stdout`). Si no proporcionas un vector `data`, se utilizará el búfer interno de trazas acumuladas.

Consulta `Profile.print` para una explicación de los argumentos de palabra clave válidos.
