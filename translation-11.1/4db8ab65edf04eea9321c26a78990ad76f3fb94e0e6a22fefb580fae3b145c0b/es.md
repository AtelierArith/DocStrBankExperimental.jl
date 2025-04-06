```
fetch(t::Task)
```

Espera a que una [`Task`](@ref) termine, luego devuelve su valor de resultado. Si la tarea falla con una excepción, se lanza una [`TaskFailedException`](@ref) (que envuelve la tarea fallida).
