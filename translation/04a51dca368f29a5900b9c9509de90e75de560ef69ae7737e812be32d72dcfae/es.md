```
open(command, stdio=devnull; write::Bool = false, read::Bool = !write)
```

Comienza a ejecutar `command` de manera asíncrona y devuelve un objeto `process::IO`. Si `read` es verdadero, entonces las lecturas del proceso provienen de la salida estándar del proceso y `stdio` especifica opcionalmente el flujo de entrada estándar del proceso. Si `write` es verdadero, entonces las escrituras van al flujo de entrada estándar del proceso y `stdio` especifica opcionalmente el flujo de salida estándar del proceso. El flujo de error estándar del proceso está conectado al `stderr` global actual.
