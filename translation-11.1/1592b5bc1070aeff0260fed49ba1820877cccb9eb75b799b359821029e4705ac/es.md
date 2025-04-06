```
@atomicreplace a.b.x esperado => deseado
@atomicreplace :sequentially_consistent a.b.x esperado => deseado
@atomicreplace :sequentially_consistent :monotonic a.b.x esperado => deseado
```

Realiza el reemplazo condicional expresado por el par de manera atómica, devolviendo los valores `(old, success::Bool)`. Donde `success` indica si el reemplazo se completó.

Esta operación se traduce en una llamada a `replaceproperty!(a.b, :x, esperado, deseado)`.

Consulta la sección [Per-field atomics](@ref man-atomics) en el manual para más detalles.

# Ejemplos

```jldoctest
julia> mutable struct Atomic{T}; @atomic x::T; end

julia> a = Atomic(1)
Atomic{Int64}(1)

julia> @atomicreplace a.x 1 => 2 # reemplaza el campo x de a con 2 si era 1, con consistencia secuencial
(old = 1, success = true)

julia> @atomic a.x # obtiene el campo x de a, con consistencia secuencial
2

julia> @atomicreplace a.x 1 => 2 # reemplaza el campo x de a con 2 si era 1, con consistencia secuencial
(old = 2, success = false)

julia> xchg = 2 => 0; # reemplaza el campo x de a con 0 si era 2, con consistencia secuencial

julia> @atomicreplace a.x xchg
(old = 2, success = true)

julia> @atomic a.x # obtiene el campo x de a, con consistencia secuencial
0
```

!!! compat "Julia 1.7"
    Esta funcionalidad requiere al menos Julia 1.7.

