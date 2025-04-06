```
arg_writers([ type = ArgWrite ]) do path::String, arg::Function
    ## configuración previa a la prueba ##
    @arg_test arg begin
        arg :: ArgWrite
        ## prueba usando `arg` ##
    end
    ## limpieza posterior a la prueba ##
end
```

La función `arg_writers` toma un bloque do, que se invoca una vez para cada tipo de escritor de prueba que `arg_write` puede manejar con un `path` temporal (inexistente) y `arg` que puede convertirse en varios tipos de argumentos escribibles que escriben en `path`. Si se proporciona el argumento opcional `type`, entonces el bloque do solo se invoca para escritores que producen argumentos de ese tipo.

El `arg` pasado al bloque do no es el valor del argumento en sí, porque algunos de los tipos de argumentos de prueba necesitan ser inicializados y finalizados para cada caso de prueba. Considera un argumento de manejador de archivo abierto: una vez que lo has usado para una prueba, no puedes usarlo de nuevo; necesitas cerrarlo y abrir el archivo nuevamente para la siguiente prueba. Esta función `arg` puede convertirse en una instancia de `ArgWrite` usando `@arg_test arg begin ... end`.

También hay un método `arg_writers` que toma un nombre de ruta como `arg_readers`:

```
arg_writers(path::AbstractString, [ type = ArgWrite ]) do arg::Function
    ## configuración previa a la prueba ##
    @arg_test arg begin
        # aquí `arg :: ArgWrite`
        ## prueba usando `arg` ##
    end
    ## limpieza posterior a la prueba ##
end
```

Este método es útil si necesitas especificar `path` en lugar de usar un nombre de ruta generado por `tempname()`. Dado que `path` se pasa desde fuera de `arg_writers`, la ruta no es un argumento para el bloque do en esta forma.
