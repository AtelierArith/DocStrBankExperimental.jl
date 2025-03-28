```
isposdef!(A) -> Bool
```

Testen Sie, ob eine Matrix positiv definit (und hermitesch) ist, indem Sie versuchen, eine Cholesky-Zerlegung von `A` durchzuführen, wobei `A` im Prozess überschrieben wird. Siehe auch [`isposdef`](@ref).

# Beispiele

```jldoctest
julia> A = [1. 2.; 2. 50.];

julia> isposdef!(A)
true

julia> A
2×2 Matrix{Float64}:
 1.0  2.0
 2.0  6.78233
```
