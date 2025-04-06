```
listen(path::AbstractString) -> PipeServer
```

Crea y escucha en un pipe nombrado / socket de dominio UNIX.

!!! note
    La longitud de la ruta en Unix está limitada a algún lugar entre 92 y 108 bytes (cf. `man unix`).

