```
isposdef(A) -> Bool
```

Überprüfen, ob eine Matrix positiv definit (und hermitesch) ist, indem versucht wird, eine Cholesky-Zerlegung von `A` durchzuführen.

Siehe auch [`isposdef!`](@ref), [`cholesky`](@ref).

# Beispiele

```jldoctest
julia> A = [1 2; 2 50]
2×2 Matrix{Int64}:
 1   2
 2  50

julia> isposdef(A)
true
```
