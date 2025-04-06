```
run(command, args...; wait::Bool = true)
```

Ejecuta un objeto de comando, construido con comillas invertidas (ver la sección de [Ejecutar Programas Externos](@ref) en el manual). Lanza un error si algo sale mal, incluyendo si el proceso sale con un estado distinto de cero (cuando `wait` es verdadero).

Los `args...` te permiten pasar descriptores de archivo al comando, y están ordenados como descriptores de archivo unix regulares (por ejemplo `stdin, stdout, stderr, FD(3), FD(4)...`).

Si `wait` es falso, el proceso se ejecuta de manera asíncrona. Puedes esperar por él más tarde y verificar su estado de salida llamando a `success` en el objeto de proceso devuelto.

Cuando `wait` es falso, los flujos de I/O del proceso se dirigen a `devnull`. Cuando `wait` es verdadero, los flujos de I/O se comparten con el proceso padre. Usa [`pipeline`](@ref) para controlar la redirección de I/O.
