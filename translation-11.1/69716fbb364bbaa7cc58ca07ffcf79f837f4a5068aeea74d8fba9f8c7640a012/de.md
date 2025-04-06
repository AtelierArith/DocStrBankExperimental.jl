```
abs2(x)
```

Quadratischer Absolutwert von `x`.

Dies kann schneller sein als `abs(x)^2`, insbesondere für komplexe Zahlen, bei denen `abs(x)` eine Quadratwurzel über [`hypot`](@ref) erfordert.

Siehe auch [`abs`](@ref), [`conj`](@ref), [`real`](@ref).

# Beispiele

```jldoctest
julia> abs2(-3)
9

julia> abs2(3.0 + 4.0im)
25.0

julia> sum(abs2, [1+2im, 3+4im])  # LinearAlgebra.norm(x)^2
30
```
