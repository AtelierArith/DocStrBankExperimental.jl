```
rmprocs(pids...; waitfor=typemax(Int))
```

Elimina los trabajadores especificados. Ten en cuenta que solo el proceso 1 puede agregar o eliminar trabajadores.

El argumento `waitfor` especifica cuánto tiempo esperar para que los trabajadores se apaguen:

  * Si no se especifica, `rmprocs` esperará hasta que todos los `pids` solicitados sean eliminados.
  * Se genera una [`ErrorException`](@ref) si no se pueden terminar todos los trabajadores antes de los segundos solicitados en `waitfor`.
  * Con un valor de `waitfor` de 0, la llamada devuelve inmediatamente con los trabajadores programados para ser eliminados en una tarea diferente. Se devuelve el objeto [`Task`](@ref) programado. El usuario debe llamar a [`wait`](@ref) en la tarea antes de invocar cualquier otra llamada paralela.

# Ejemplos

```julia-repl
$ julia -p 5

julia> t = rmprocs(2, 3, waitfor=0)
Task (runnable) @0x0000000107c718d0

julia> wait(t)

julia> workers()
3-element Array{Int64,1}:
 4
 5
 6
```
