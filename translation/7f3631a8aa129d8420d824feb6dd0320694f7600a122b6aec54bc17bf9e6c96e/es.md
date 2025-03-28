```
open(fd::OS_HANDLE) -> IO
```

Toma un descriptor de archivo en bruto, envuélvelo en un tipo IO consciente de Julia y toma posesión del manejador fd. Llama a `open(Libc.dup(fd))` para evitar la captura de propiedad del manejador original.

!!! warning
    No llames a esto en un manejador que ya está en posesión de otra parte del sistema.

