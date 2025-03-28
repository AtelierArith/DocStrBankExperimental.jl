```
eigvals!(A, B; sortby) -> values
```

Identique à [`eigvals`](@ref), mais économise de l'espace en écrasant l'entrée `A` (et `B`), au lieu de créer des copies.

!!! note
    Les matrices d'entrée `A` et `B` ne contiendront pas leurs valeurs propres après l'appel de `eigvals!`. Elles sont utilisées comme espaces de travail.


# Exemples

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
