```
Base.split_rest(collection, n::Int[, itr_state]) -> (rest_but_n, last_n)
```

Función genérica para dividir la cola de `collection`, comenzando desde un estado de iteración específico `itr_state`. Devuelve una tupla de dos nuevas colecciones. La primera contiene todos los elementos de la cola menos los `n` últimos, que constituyen la segunda colección.

El tipo de la primera colección generalmente sigue el de [`Base.rest`](@ref), excepto que el caso por defecto no es perezoso, sino que se recopila de manera ansiosa en un vector.

Se puede sobrecargar para tipos de colección definidos por el usuario para personalizar el comportamiento de [slurping en asignaciones](@ref destructuring-assignment) en posición no final, como `a, b..., c = collection`.

!!! compat "Julia 1.9"
    `Base.split_rest` requiere al menos Julia 1.9.


Véase también: [`Base.rest`](@ref).

# Ejemplos

```jldoctest
julia> a = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> first, state = iterate(a)
(1, 2)

julia> first, Base.split_rest(a, 1, state)
(1, ([3, 2], [4]))
```
