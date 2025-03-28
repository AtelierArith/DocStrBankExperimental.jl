```
eigvals!(A, B; sortby) -> values
```

Gleich wie [`eigvals`](@ref), aber spart Speicherplatz, indem die Eingabe `A` (und `B`) überschrieben wird, anstatt Kopien zu erstellen.

!!! Hinweis     Die Eingabematrizen `A` und `B` enthalten nach dem Aufruf von `eigvals!` ihre Eigenwerte nicht mehr. Sie werden als Arbeitsräume verwendet.

# Beispiele

```jldoctest
julia> A = [1. 0.; 0. -1.]
2×2 Matrix{Float64}:
 1.0   0.0
 0.0  -1.0

julia> B = [0. 1.; 1. 0.]
2×2 Matrix{Float64}:
 0.0  1.0
 1.0  0.0

julia> eigvals!(A, B)
2-element Vector{ComplexF64}:
 0.0 - 1.0im
 0.0 + 1.0im

julia> A
2×2 Matrix{Float64}:
 -0.0  -1.0
  1.0  -0.0

julia> B
2×2 Matrix{Float64}:
 1.0  0.0
 0.0  1.0
```
