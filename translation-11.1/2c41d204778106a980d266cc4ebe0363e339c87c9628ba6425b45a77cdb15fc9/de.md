```
tan(A::AbstractMatrix)
```

Berechne den Matrizen-Tangens einer quadratischen Matrix `A`.

Wenn `A` symmetrisch oder hermitesch ist, wird ihre Eigenzerlegung ([`eigen`](@ref)) verwendet, um den Tangens zu berechnen. Andernfalls wird der Tangens durch den Aufruf von [`exp`](@ref) bestimmt.

# Beispiele

```jldoctest
julia> tan(fill(1.0, (2,2)))
2×2 Matrix{Float64}:
 -1.09252  -1.09252
 -1.09252  -1.09252
```
