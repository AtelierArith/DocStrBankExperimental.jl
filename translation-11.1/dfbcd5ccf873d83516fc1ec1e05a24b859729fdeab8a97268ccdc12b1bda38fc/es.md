```
arg_readers(arg :: AbstractString, [ type = ArgRead ]) do arg::Function
    ## configuración previa a la prueba ##
    @arg_test arg begin
        arg :: ArgRead
        ## prueba usando `arg` ##
    end
    ## limpieza posterior a la prueba ##
end
```

La función `arg_readers` toma una ruta a ser leída y un bloque do de un solo argumento, que se invoca una vez para cada tipo de lector de prueba que `arg_read` puede manejar. Si se proporciona el argumento opcional `type`, entonces el bloque do solo se invoca para los lectores que producen argumentos de ese tipo.

El `arg` pasado al bloque do no es el valor del argumento en sí, porque algunos de los tipos de argumentos de prueba necesitan ser inicializados y finalizados para cada caso de prueba. Considera un argumento de manejador de archivo abierto: una vez que lo has usado para una prueba, no puedes usarlo de nuevo; necesitas cerrarlo y abrir el archivo nuevamente para la siguiente prueba. Esta función `arg` puede convertirse en una instancia de `ArgRead` usando `@arg_test arg begin ... end`.
