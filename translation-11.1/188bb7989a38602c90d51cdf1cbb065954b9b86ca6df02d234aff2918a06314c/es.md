```
@timev expr
@timev "description" expr
```

Esta es una versión detallada de la macro `@time`. Primero imprime la misma información que `@time`, luego cualquier contador de asignación de memoria no cero, y luego devuelve el valor de la expresión.

Opcionalmente, proporciona una cadena de descripción para imprimir antes del informe de tiempo.

!!! compat "Julia 1.8"
    La opción de agregar una descripción se introdujo en Julia 1.8.


Véase también [`@time`](@ref), [`@timed`](@ref), [`@elapsed`](@ref), [`@allocated`](@ref), y [`@allocations`](@ref).

```julia-repl
julia> x = rand(10,10);

julia> @timev x * x;
  0.546770 seconds (2.20 M allocations: 116.632 MiB, 4.23% gc time, 99.94% compilation time)
elapsed time (ns): 546769547
gc time (ns):      23115606
bytes allocated:   122297811
pool allocs:       2197930
non-pool GC allocs:1327
malloc() calls:    36
realloc() calls:   5
GC pauses:         3

julia> @timev x * x;
  0.000010 seconds (1 allocation: 896 bytes)
elapsed time (ns): 9848
bytes allocated:   896
pool allocs:       1
```
