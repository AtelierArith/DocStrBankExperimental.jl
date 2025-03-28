```
cumsum(itr)
```

Kumulative Summe eines Iterators.

Siehe auch [`accumulate`](@ref), um Funktionen anzuwenden, die nicht `+` sind.

!!! compat "Julia 1.5"
    `cumsum` auf einem Nicht-Array-Iterator erfordert mindestens Julia 1.5.


# Beispiele

```jldoctest
julia> cumsum(1:3)
3-element Vector{Int64}:
 1
 3
 6

julia> cumsum((true, false, true, false, true))
(1, 1, 2, 2, 3)

julia> cumsum(fill(1, 2) for i in 1:3)
3-element Vector{Vector{Int64}}:
 [1, 1]
 [2, 2]
 [3, 3]
```
