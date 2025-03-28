```
cos(A::AbstractMatrix)
```

Berechne den Matrix-Cosinus einer quadratischen Matrix `A`.

Wenn `A` symmetrisch oder hermitesch ist, wird ihre Eigenzerlegung ([`eigen`](@ref)) verwendet, um den Cosinus zu berechnen. Andernfalls wird der Cosinus durch den Aufruf von [`exp`](@ref) bestimmt.

# Beispiele

```jldoctest
julia> cos(fill(1.0, (2,2)))
2×2 Matrix{Float64}:
  0.291927  -0.708073
 -0.708073   0.291927
```
