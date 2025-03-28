```
@atomic var
@atomic order ex
```

Marque `var` o `ex` como si se estuviera realizando de manera atómica, si `ex` es una expresión admitida. Si no se especifica `order`, por defecto es :sequentially_consistent.

```
@atomic a.b.x = new
@atomic a.b.x += addend
@atomic :release a.b.x = new
@atomic :acquire_release a.b.x += addend
```

Realice la operación de almacenamiento expresada a la derecha de manera atómica y devuelva el nuevo valor.

Con `=`, esta operación se traduce en una llamada a `setproperty!(a.b, :x, new)`. Con cualquier operador también, esta operación se traduce en una llamada a `modifyproperty!(a.b, :x, +, addend)[2]`.

```
@atomic a.b.x max arg2
@atomic a.b.x + arg2
@atomic max(a.b.x, arg2)
@atomic :acquire_release max(a.b.x, arg2)
@atomic :acquire_release a.b.x + arg2
@atomic :acquire_release a.b.x max arg2
```

Realice la operación binaria expresada a la derecha de manera atómica. Almacene el resultado en el campo del primer argumento y devuelva los valores `(old, new)`.

Esta operación se traduce en una llamada a `modifyproperty!(a.b, :x, func, arg2)`.

Consulte la sección [Per-field atomics](@ref man-atomics) en el manual para más detalles.

# Ejemplos

```jldoctest
julia> mutable struct Atomic{T}; @atomic x::T; end

julia> a = Atomic(1)
Atomic{Int64}(1)

julia> @atomic a.x # obtener el campo x de a, con consistencia secuencial
1

julia> @atomic :sequentially_consistent a.x = 2 # establecer el campo x de a, con consistencia secuencial
2

julia> @atomic a.x += 1 # incrementar el campo x de a, con consistencia secuencial
3

julia> @atomic a.x + 1 # incrementar el campo x de a, con consistencia secuencial
3 => 4

julia> @atomic a.x # obtener el campo x de a, con consistencia secuencial
4

julia> @atomic max(a.x, 10) # cambiar el campo x de a al valor máximo, con consistencia secuencial
4 => 10

julia> @atomic a.x max 5 # nuevamente cambiar el campo x de a al valor máximo, con consistencia secuencial
10 => 10
```

!!! compat "Julia 1.7"
    Esta funcionalidad requiere al menos Julia 1.7.

