```
print([io::IO = stdout,] [data::Vector = fetch()], [lidict::Union{LineInfoDict, LineInfoFlatDict} = getdict(data)]; kwargs...)
```

Imprime los resultados de perfilado en `io` (por defecto, `stdout`). Si no proporcionas un vector `data`, se utilizará el búfer interno de trazas de pila acumuladas.

Los argumentos de palabra clave pueden ser cualquier combinación de:

  * `format` – Determina si las trazas de pila se imprimen con (por defecto, `:tree`) o sin (`:flat`) sangrías que indican la estructura del árbol.
  * `C` – Si es `true`, se muestran las trazas de pila del código C y Fortran (normalmente están excluidas).
  * `combine` – Si es `true` (por defecto), se fusionan los punteros de instrucción que corresponden a la misma línea de código.
  * `maxdepth` – Limita la profundidad superior a `maxdepth` en el formato `:tree`.
  * `sortedby` – Controla el orden en el formato `:flat`. `:filefuncline` (por defecto) ordena por la línea de origen, `:count` ordena en orden del número de muestras recolectadas, y `:overhead` ordena por el número de muestras incurridas por cada función por sí misma.
  * `groupby` – Controla la agrupación sobre tareas e hilos, o sin agrupación. Las opciones son `:none` (por defecto), `:thread`, `:task`, `[:thread, :task]`, o `[:task, :thread]` donde los dos últimos proporcionan agrupación anidada.
  * `noisefloor` – Limita los marcos que exceden el umbral de ruido heurístico de la muestra (solo se aplica al formato `:tree`). Un valor sugerido para probar esto es 2.0 (el valor por defecto es 0). Este parámetro oculta muestras para las cuales `n <= noisefloor * √N`, donde `n` es el número de muestras en esta línea, y `N` es el número de muestras para el llamado.
  * `mincount` – Limita la impresión solo a aquellas líneas con al menos `mincount` ocurrencias.
  * `recur` – Controla el manejo de la recursión en el formato `:tree`. `:off` (por defecto) imprime el árbol como normal. `:flat` en su lugar comprime cualquier recursión (por ip), mostrando el efecto aproximado de convertir cualquier auto-recursión en un iterador. `:flatc` hace lo mismo pero también incluye la colapsación de marcos C (puede hacer cosas extrañas alrededor de `jl_apply`).
  * `threads::Union{Int,AbstractVector{Int}}` – Especifica qué hilos incluir en las instantáneas del informe. Ten en cuenta que esto no controla qué hilos se recolectan muestras (que también pueden haberse recolectado en otra máquina).
  * `tasks::Union{Int,AbstractVector{Int}}` – Especifica qué tareas incluir en las instantáneas del informe. Ten en cuenta que esto no controla en qué tareas se recolectan muestras.

!!! compat "Julia 1.8"
    Los argumentos de palabra clave `groupby`, `threads` y `tasks` se introdujeron en Julia 1.8.


!!! note
    El perfilado en Windows está limitado al hilo principal. Otros hilos no han sido muestreados y no aparecerán en el informe.

