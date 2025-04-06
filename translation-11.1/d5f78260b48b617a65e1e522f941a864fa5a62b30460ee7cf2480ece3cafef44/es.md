```
start_worker([out::IO=stdout], cookie::AbstractString=readline(stdin); close_stdin::Bool=true, stderr_to_stdout::Bool=true)
```

`start_worker` es una función interna que es el punto de entrada predeterminado para los procesos de trabajo que se conectan a través de TCP/IP. Configura el proceso como un trabajador del clúster de Julia.

La información de host:puerto se escribe en el flujo `out` (por defecto en stdout).

La función lee la cookie de stdin si es necesario, y escucha en un puerto libre (o si se especifica, el puerto en la opción de línea de comandos `--bind-to`) y programa tareas para procesar conexiones y solicitudes TCP entrantes. También (opcionalmente) cierra stdin y redirige stderr a stdout.

No devuelve.
