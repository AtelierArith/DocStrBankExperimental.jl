```
@atomiconce a.b.x = value
@atomiconce :sequentially_consistent a.b.x = value
@atomiconce :sequentially_consistent :monotonic a.b.x = value
```

Realiza la asignación condicional de value de manera atómica si anteriormente no estaba establecido, devolviendo el valor `success::Bool`. Donde `success` indica si la asignación se completó.

Esta operación se traduce en una llamada a `setpropertyonce!(a.b, :x, value)`.

Consulta la sección [Per-field atomics](@ref man-atomics) en el manual para más detalles.

# Ejemplos

```jldoctest
julia> mutable struct AtomicOnce
           @atomic x
           AtomicOnce() = new()
       end

julia> a = AtomicOnce()
AtomicOnce(#undef)

julia> @atomiconce a.x = 1 # establece el campo x de a en 1, si no está establecido, con consistencia secuencial
true

julia> @atomic a.x # obtiene el campo x de a, con consistencia secuencial
1

julia> @atomiconce a.x = 1 # establece el campo x de a en 1, si no está establecido, con consistencia secuencial
false
```

!!! compat "Julia 1.11"
    Esta funcionalidad requiere al menos Julia 1.11.

