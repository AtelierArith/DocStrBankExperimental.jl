```
VecOrMat{T}
```

Type d'union de [`Vector{T}`](@ref) et [`Matrix{T}`](@ref) qui permet aux fonctions d'accepter soit une matrice, soit un vecteur.

# Exemples

```jldoctest
julia> Vector{Float64} <: VecOrMat{Float64}
true

julia> Matrix{Float64} <: VecOrMat{Float64}
true

julia> Array{Float64, 3} <: VecOrMat{Float64}
false
```
