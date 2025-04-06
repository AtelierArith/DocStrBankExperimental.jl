```
@atomicswap a.b.x = new
@atomicswap :sequentially_consistent a.b.x = new
```

Almacena `new` en `a.b.x` y devuelve el valor antiguo de `a.b.x`.

Esta operación se traduce en una llamada a `swapproperty!(a.b, :x, new)`.

Consulta la sección [Per-field atomics](@ref man-atomics) en el manual para más detalles.

# Ejemplos

```jldoctest
julia> mutable struct Atomic{T}; @atomic x::T; end

julia> a = Atomic(1)
Atomic{Int64}(1)

julia> @atomicswap a.x = 2+2 # reemplaza el campo x de a con 4, con consistencia secuencial
1

julia> @atomic a.x # obtiene el campo x de a, con consistencia secuencial
4
```

!!! compat "Julia 1.7"
    Esta funcionalidad requiere al menos Julia 1.7.

