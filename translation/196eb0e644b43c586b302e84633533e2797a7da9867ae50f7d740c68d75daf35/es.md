```
isbitstype(T)
```

Devuelve `true` si el tipo `T` es un tipo de "datos simples", lo que significa que es inmutable y no contiene referencias a otros valores, solo tipos `primitivos` y otros tipos `isbitstype`. Ejemplos típicos son tipos numéricos como [`UInt8`](@ref), [`Float64`](@ref) y [`Complex{Float64}`](@ref). Esta categoría de tipos es significativa ya que son válidos como parámetros de tipo, pueden no rastrear el estado de [`isdefined`](@ref) / [`isassigned`](@ref), y tienen un diseño definido que es compatible con C. Si `T` no es un tipo, entonces devuelve `false`.

Véase también [`isbits`](@ref), [`isprimitivetype`](@ref), [`ismutable`](@ref).

# Ejemplos

```jldoctest
julia> isbitstype(Complex{Float64})
true

julia> isbitstype(Complex)
false
```
