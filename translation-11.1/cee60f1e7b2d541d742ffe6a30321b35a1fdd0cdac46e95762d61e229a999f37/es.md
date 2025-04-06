```
connect(path::AbstractString) -> PipeEndpoint
```

Conéctese al pipe nombrado / socket de dominio UNIX en `path`.

!!! note
    La longitud de la ruta en Unix está limitada a algún lugar entre 92 y 108 bytes (cf. `man unix`).

