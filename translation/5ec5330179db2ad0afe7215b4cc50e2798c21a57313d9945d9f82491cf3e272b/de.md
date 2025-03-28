```
mod(x::Integer, r::AbstractUnitRange)
```

Finde `y` im Bereich `r`, so dass $x ≡ y (mod n)$, wobei `n = length(r)`, d.h. `y = mod(x - first(r), n) + first(r)`.

Siehe auch [`mod1`](@ref).

# Beispiele

```jldoctest
julia> mod(0, Base.OneTo(3))  # mod1(0, 3)
3

julia> mod(3, 0:2)  # mod(3, 3)
0
```

!!! compat "Julia 1.3"
    Diese Methode erfordert mindestens Julia 1.3.

