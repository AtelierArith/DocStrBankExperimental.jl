```
addprocs(manager::ClusterManager; kwargs...) -> Lista de identificadores de procesos
```

Lanza procesos de trabajo a través del administrador de clústeres especificado.

Por ejemplo, los clústeres Beowulf son compatibles a través de un administrador de clústeres personalizado implementado en el paquete `ClusterManagers.jl`.

El número de segundos que un nuevo trabajador espera para el establecimiento de la conexión desde el maestro se puede especificar a través de la variable `JULIA_WORKER_TIMEOUT` en el entorno del proceso de trabajo. Relevante solo cuando se utiliza TCP/IP como transporte.

Para lanzar trabajadores sin bloquear el REPL, o la función que contiene si se lanzan trabajadores programáticamente, ejecuta `addprocs` en su propia tarea.

# Ejemplos

```julia
# En clústeres ocupados, llama a `addprocs` de forma asíncrona
t = @async addprocs(...)
```

```julia
# Utiliza trabajadores a medida que se conectan
if nprocs() > 1   # Asegúrate de que al menos un nuevo trabajador esté disponible
   ....   # realiza ejecución distribuida
end
```

```julia
# Recupera los IDs de los trabajadores recién lanzados, o cualquier mensaje de error
if istaskdone(t)   # Verifica si `addprocs` ha completado para asegurar que `fetch` no bloquee
    if nworkers() == N
        new_pids = fetch(t)
    else
        fetch(t)
    end
end
```
