```
@elapsed
```

Una macro para evaluar una expresión, descartando el valor resultante, en su lugar devolviendo el número de segundos que tomó ejecutarse como un número de punto flotante.

En algunos casos, el sistema mirará dentro de la expresión `@elapsed` y compilará parte del código llamado antes de que comience la ejecución de la expresión de nivel superior. Cuando eso sucede, parte del tiempo de compilación no se contará. Para incluir este tiempo, puedes ejecutar `@elapsed @eval ...`.

Consulta también [`@time`](@ref), [`@timev`](@ref), [`@timed`](@ref), [`@allocated`](@ref), y [`@allocations`](@ref).

```julia-repl
julia> @elapsed sleep(0.3)
0.301391426
```
