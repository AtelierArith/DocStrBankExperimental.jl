```
allunique(itr) -> Bool
allunique(f, itr) -> Bool
```

Devuelve `true` si todos los valores de `itr` son distintos cuando se comparan con [`isequal`](@ref). O si todos los de `[f(x) for x in itr]` son distintos, para el segundo método.

Ten en cuenta que `allunique(f, itr)` puede llamar a `f` menos de `length(itr)` veces. El número preciso de llamadas se considera un detalle de implementación.

`allunique` puede utilizar una implementación especializada cuando la entrada está ordenada.

Consulta también: [`unique`](@ref), [`issorted`](@ref), [`allequal`](@ref).

!!! compat "Julia 1.11"
    El método `allunique(f, itr)` requiere al menos Julia 1.11.


# Ejemplos

```jldoctest
julia> allunique([1, 2, 3])
true

julia> allunique([1, 2, 1, 2])
false

julia> allunique(Real[1, 1.0, 2])
false

julia> allunique([NaN, 2.0, NaN, 4.0])
false

julia> allunique(abs, [1, -1, 2])
false
```
