```
LinearAlgebra.checksquare(A)
```

Überprüfen Sie, ob eine Matrix quadratisch ist, und geben Sie dann ihre gemeinsame Dimension zurück. Bei mehreren Argumenten geben Sie einen Vektor zurück.

# Beispiele

```jldoctest
julia> A = fill(1, (4,4)); B = fill(1, (5,5));

julia> LinearAlgebra.checksquare(A, B)
2-element Vector{Int64}:
 4
 5
```
