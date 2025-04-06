```
muladd(A, y, z)
```

Kombinierte Multiplikation-Addition, `A*y .+ z`, für Matrix-Matrix- oder Matrix-Vektor-Multiplikation. Das Ergebnis hat immer die gleiche Größe wie `A*y`, aber `z` kann kleiner oder ein Skalar sein.

!!! compat "Julia 1.6"
    Diese Methoden erfordern Julia 1.6 oder später.


# Beispiele

```jldoctest
julia> A=[1.0 2.0; 3.0 4.0]; B=[1.0 1.0; 1.0 1.0]; z=[0, 100];

julia> muladd(A, B, z)
2×2 Matrix{Float64}:
   3.0    3.0
 107.0  107.0
```
