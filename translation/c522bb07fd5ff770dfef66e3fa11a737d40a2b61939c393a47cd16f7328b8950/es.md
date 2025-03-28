```
one(x)
one(T::type)
```

Devuelve una identidad multiplicativa para `x`: un valor tal que `one(x)*x == x*one(x) == x`. Alternativamente, `one(T)` puede tomar un tipo `T`, en cuyo caso `one` devuelve una identidad multiplicativa para cualquier `x` del tipo `T`.

Si es posible, `one(x)` devuelve un valor del mismo tipo que `x`, y `one(T)` devuelve un valor del tipo `T`. Sin embargo, esto puede no ser el caso para tipos que representan cantidades con dimensiones (por ejemplo, tiempo en días), ya que la identidad multiplicativa debe ser adimensional. En ese caso, `one(x)` debería devolver un valor de identidad de la misma precisión (y forma, para matrices) que `x`.

Si deseas una cantidad que sea del mismo tipo que `x`, o del tipo `T`, incluso si `x` tiene dimensiones, utiliza [`oneunit`](@ref) en su lugar.

Consulta también la función [`identity`](@ref), y `I` en [`LinearAlgebra`](@ref man-linalg) para la matriz identidad.

# Ejemplos

```jldoctest
julia> one(3.7)
1.0

julia> one(Int)
1

julia> import Dates; one(Dates.Day(1))
1
```
