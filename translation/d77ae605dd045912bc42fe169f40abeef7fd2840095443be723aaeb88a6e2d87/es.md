```
Threads.threadid() -> Int
```

Obtiene el número de ID del hilo de ejecución actual. El hilo maestro tiene ID `1`.

# Ejemplos

```julia-repl
julia> Threads.threadid()
1

julia> Threads.@threads for i in 1:4
          println(Threads.threadid())
       end
4
2
5
4
```

!!! nota
    El hilo en el que se ejecuta una tarea puede cambiar si la tarea cede, lo que se conoce como [`Migración de Tareas`](@ref man-task-migration). Por esta razón, en la mayoría de los casos no es seguro usar `threadid()` para indexar, por ejemplo, un vector de objetos de búfer o con estado.

