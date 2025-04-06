```
sortperm!(ix, A; alg::Algorithm=DEFAULT_UNSTABLE, lt=isless, by=identity, rev::Bool=false, order::Ordering=Forward, [dims::Integer])
```

Wie [`sortperm`](@ref), aber akzeptiert einen vorab zugewiesenen Indexvektor oder -array `ix` mit denselben `axes` wie `A`. `ix` wird initialisiert, um die Werte `LinearIndices(A)` zu enthalten.

!!! warning
    Das Verhalten kann unerwartet sein, wenn ein mutierter Parameter Speicher mit einem anderen Parameter teilt.


!!! compat "Julia 1.9"
    Die Methode, die `dims` akzeptiert, erfordert mindestens Julia 1.9.


# Beispiele

```jldoctest
julia> v = [3, 1, 2]; p = zeros(Int, 3);

julia> sortperm!(p, v); p
3-element Vector{Int64}:
 2
 3
 1

julia> v[p]
3-element Vector{Int64}:
 1
 2
 3

julia> A = [8 7; 5 6]; p = zeros(Int,2, 2);

julia> sortperm!(p, A; dims=1); p
2×2 Matrix{Int64}:
 2  4
 1  3

julia> sortperm!(p, A; dims=2); p
2×2 Matrix{Int64}:
 3  1
 2  4
```
