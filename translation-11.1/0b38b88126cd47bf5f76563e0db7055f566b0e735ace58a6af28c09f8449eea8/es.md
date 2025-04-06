```
AbstractWorkerPool
```

Supertipo para grupos de trabajadores como [`WorkerPool`](@ref) y [`CachingPool`](@ref). Un `AbstractWorkerPool` debe implementar:

  * [`push!`](@ref) - agregar un nuevo trabajador al grupo general (disponible + ocupado)
  * [`put!`](@ref) - devolver un trabajador al grupo disponible
  * [`take!`](@ref) - tomar un trabajador del grupo disponible (para ser utilizado en la ejecución de funciones remotas)
  * [`length`](@ref) - número de trabajadores disponibles en el grupo general
  * [`isready`](@ref) - devolver falso si un `take!` en el grupo bloquearía, de lo contrario, verdadero

Las implementaciones predeterminadas de lo anterior (en un `AbstractWorkerPool`) requieren campos

  * `channel::Channel{Int}`
  * `workers::Set{Int}`

donde `channel` contiene pids de trabajadores libres y `workers` es el conjunto de todos los trabajadores asociados con este grupo.
