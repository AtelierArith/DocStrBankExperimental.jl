```
eigvals!(A; permute::Bool=true, scale::Bool=true, sortby) -> valeurs
```

Identique à [`eigvals`](@ref), mais économise de l'espace en écrasant l'entrée `A`, au lieu de créer une copie. Les mots-clés `permute`, `scale` et `sortby` sont les mêmes que pour [`eigen`](@ref).

!!! note
    La matrice d'entrée `A` ne contiendra pas ses valeurs propres après que `eigvals!` ait été appelé dessus - `A` est utilisé comme espace de travail.


# Exemples

```jldoctest
julia> A = [1. 2.; 3. 4.]
2×2 Matrix{Float64}:
 1.0  2.0
 3.0  4.0

julia> eigvals!(A)
2-element Vector{Float64}:
 -0.3722813232690143
  5.372281323269014

julia> A
2×2 Matrix{Float64}:
 -0.372281  -1.0
  0.0        5.37228
```
