```
parse_pidfile(file::Union{IO, String}) => (pid, hostname, age)
```

Intenta analizar nuestro formato de pidfile, reemplazando un elemento con (0, "", 0.0), respectivamente, para cualquier lectura que falló.
