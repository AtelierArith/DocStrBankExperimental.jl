```
notify(condition, val=nothing; all=true, error=false)
```

Despierta las tareas que están esperando una condición, pasándoles `val`. Si `all` es `true` (el valor predeterminado), se despiertan todas las tareas en espera; de lo contrario, solo se despierta una. Si `error` es `true`, el valor pasado se eleva como una excepción en las tareas despertadas.

Devuelve el conteo de tareas despertadas. Devuelve 0 si no hay tareas esperando en `condition`.
