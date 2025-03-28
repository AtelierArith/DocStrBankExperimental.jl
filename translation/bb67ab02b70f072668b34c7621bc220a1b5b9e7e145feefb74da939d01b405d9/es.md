```
allequal(itr) -> Bool
allequal(f, itr) -> Bool
```

Devuelve `true` si todos los valores de `itr` son iguales cuando se comparan con [`isequal`](@ref). O si todos los de `[f(x) for x in itr]` son iguales, para el segundo método.

Ten en cuenta que `allequal(f, itr)` puede llamar a `f` menos de `length(itr)` veces. El número preciso de llamadas se considera un detalle de implementación.

Ver también: [`unique`](@ref), [`allunique`](@ref).

!!! compat "Julia 1.8"
    La función `allequal` requiere al menos Julia 1.8.


!!! compat "Julia 1.11"
    El método `allequal(f, itr)` requiere al menos Julia 1.11.


# Ejemplos

```jldoctest
julia> allequal([])
true

julia> allequal([1])
true

julia> allequal([1, 1])
true

julia> allequal([1, 2])
false

julia> allequal(Dict(:a => 1, :b => 1))
false

julia> allequal(abs2, [1, -1])
true
```
