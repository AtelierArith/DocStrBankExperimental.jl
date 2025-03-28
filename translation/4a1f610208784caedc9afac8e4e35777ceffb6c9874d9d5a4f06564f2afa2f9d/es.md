```
current_exceptions(task::Task=current_task(); [backtrace::Bool=true])
```

Obtiene la pila de excepciones que se están manejando actualmente. Para bloques de captura anidados, puede haber más de una excepción actual, en cuyo caso la excepción lanzada más recientemente está al final de la pila. La pila se devuelve como un `ExceptionStack`, que es un AbstractVector de tuplas nombradas `(exception,backtrace)`. Si `backtrace` es falso, la traza de la pila en cada par se establecerá en `nothing`.

Pasar explícitamente `task` devolverá la pila de excepciones actual en una tarea arbitraria. Esto es útil para inspeccionar tareas que han fallado debido a excepciones no capturadas.

!!! compat "Julia 1.7"
    Esta función se conocía con el nombre experimental `catch_stack()` en Julia 1.1–1.6, y tenía un tipo de retorno de Vector de tuplas simple.

