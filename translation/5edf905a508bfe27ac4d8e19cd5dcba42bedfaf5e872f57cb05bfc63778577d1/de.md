```
ispow2(n::Number) -> Bool
```

Überprüfen, ob `n` eine ganze Potenz von zwei ist.

Siehe auch [`count_ones`](@ref), [`prevpow`](@ref), [`nextpow`](@ref).

# Beispiele

```jldoctest
julia> ispow2(4)
true

julia> ispow2(5)
false

julia> ispow2(4.5)
false

julia> ispow2(0.25)
true

julia> ispow2(1//8)
true
```

!!! compat "Julia 1.6"
    Unterstützung für nicht-`Integer` Argumente wurde in Julia 1.6 hinzugefügt.

