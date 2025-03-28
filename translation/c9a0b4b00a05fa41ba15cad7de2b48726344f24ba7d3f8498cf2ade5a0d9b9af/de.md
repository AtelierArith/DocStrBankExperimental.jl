```
reverse(A; dims=:)
```

Kehrt `A` entlang der Dimension `dims` um, die eine ganze Zahl (eine einzelne Dimension), ein Tupel von ganzen Zahlen (ein Tupel von Dimensionen) oder `:` (um entlang aller Dimensionen umzukehren, die Standardoption) sein kann. Siehe auch [`reverse!`](@ref) für die Umkehrung in-place.

# Beispiele

```jldoctest
julia> b = Int64[1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> reverse(b, dims=2)
2×2 Matrix{Int64}:
 2  1
 4  3

julia> reverse(b)
2×2 Matrix{Int64}:
 4  3
 2  1
```

!!! compat "Julia 1.6"
    Vor Julia 1.6 werden nur einzelne ganze Zahlen für `dims` in `reverse` unterstützt.

