```
cumprod(itr)
```

Kumulative Produkt eines Iterators.

Siehe auch [`cumprod!`](@ref), [`accumulate`](@ref), [`cumsum`](@ref).

!!! compat "Julia 1.5"
    `cumprod` auf einem Nicht-Array-Iterator erfordert mindestens Julia 1.5.


# Beispiele

```jldoctest
julia> cumprod(fill(1//2, 3))
3-element Vector{Rational{Int64}}:
 1//2
 1//4
 1//8

julia> cumprod((1, 2, 1, 3, 1))
(1, 2, 2, 6, 6)

julia> cumprod("julia")
5-element Vector{String}:
 "j"
 "ju"
 "jul"
 "juli"
 "julia"
```
