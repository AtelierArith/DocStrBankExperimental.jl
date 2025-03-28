```
inv(x)
```

Gibt das multiplikative Inverse von `x` zurück, so dass `x*inv(x)` oder `inv(x)*x` [`one(x)`](@ref) (die multiplikative Identität) bis auf Rundungsfehler ergibt.

Wenn `x` eine Zahl ist, ist dies im Wesentlichen dasselbe wie `one(x)/x`, aber für einige Typen kann `inv(x)` etwas effizienter sein.

# Beispiele

```jldoctest
julia> inv(2)
0.5

julia> inv(1 + 2im)
0.2 - 0.4im

julia> inv(1 + 2im) * (1 + 2im)
1.0 + 0.0im

julia> inv(2//3)
3//2
```

!!! compat "Julia 1.2"
    `inv(::Missing)` erfordert mindestens Julia 1.2.

