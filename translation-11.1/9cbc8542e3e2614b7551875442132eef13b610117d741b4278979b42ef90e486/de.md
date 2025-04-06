```
sin(A::AbstractMatrix)
```

Berechne den Matrizensinus einer quadratischen Matrix `A`.

Wenn `A` symmetrisch oder hermitesch ist, wird ihre Eigenzerlegung ([`eigen`](@ref)) verwendet, um den Sinus zu berechnen. Andernfalls wird der Sinus durch den Aufruf von [`exp`](@ref) bestimmt.

# Beispiele

```jldoctest
julia> sin(fill(1.0, (2,2)))
2×2 Matrix{Float64}:
 0.454649  0.454649
 0.454649  0.454649
```
