```
pipeline(command; stdin, stdout, stderr, append=false)
```

Redirigir I/O hacia o desde el `command` dado. Los argumentos de palabra clave especifican cuáles de los flujos del comando deben ser redirigidos. `append` controla si la salida del archivo se agrega al archivo. Esta es una versión más general de la función `pipeline` de 2 argumentos. `pipeline(from, to)` es equivalente a `pipeline(from, stdout=to)` cuando `from` es un comando, y a `pipeline(to, stdin=from)` cuando `from` es otro tipo de fuente de datos.

**Ejemplos**:

```julia
run(pipeline(`dothings`, stdout="out.txt", stderr="errs.txt"))
run(pipeline(`update`, stdout="log.txt", append=true))
```
