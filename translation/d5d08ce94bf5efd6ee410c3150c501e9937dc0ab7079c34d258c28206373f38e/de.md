```
iszero(x)
```

Gibt `true` zurück, wenn `x == zero(x)`; wenn `x` ein Array ist, überprüft dies, ob alle Elemente von `x` null sind.

Siehe auch: [`isone`](@ref), [`isinteger`](@ref), [`isfinite`](@ref), [`isnan`](@ref).

# Beispiele

```jldoctest
julia> iszero(0.0)
true

julia> iszero([1, 9, 0])
false

julia> iszero([false, 0, 0])
true
```
