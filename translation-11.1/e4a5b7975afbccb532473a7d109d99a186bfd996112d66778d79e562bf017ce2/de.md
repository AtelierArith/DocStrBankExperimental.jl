```
BoundsError([a],[i])
```

Ein Indexierungsoperation in ein Array, `a`, versuchte, auf ein Element außerhalb der Grenzen am Index `i` zuzugreifen.

# Beispiele

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> A = fill(1.0, 7);

julia> A[8]
ERROR: BoundsError: Versuch, auf 7-element Vector{Float64} am Index [8] zuzugreifen


julia> B = fill(1.0, (2,3));

julia> B[2, 4]
ERROR: BoundsError: Versuch, auf 2×3 Matrix{Float64} am Index [2, 4] zuzugreifen


julia> B[9]
ERROR: BoundsError: Versuch, auf 2×3 Matrix{Float64} am Index [9] zuzugreifen

```
