```
mod(x::Integer, r::AbstractUnitRange)
```

Encuentra `y` en el rango `r` tal que $x ≡ y (mod n)$, donde `n = length(r)`, es decir, `y = mod(x - first(r), n) + first(r)`.

Ver también [`mod1`](@ref).

# Ejemplos

```jldoctest
julia> mod(0, Base.OneTo(3))  # mod1(0, 3)
3

julia> mod(3, 0:2)  # mod(3, 3)
0
```

!!! compat "Julia 1.3"
    Este método requiere al menos Julia 1.3.

