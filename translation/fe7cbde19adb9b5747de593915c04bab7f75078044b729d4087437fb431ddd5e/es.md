```
VecOrMat{T}
```

Tipo de unión de [`Vector{T}`](@ref) y [`Matrix{T}`](@ref) que permite que las funciones acepten ya sea una Matriz o un Vector.

# Ejemplos

```jldoctest
julia> Vector{Float64} <: VecOrMat{Float64}
true

julia> Matrix{Float64} <: VecOrMat{Float64}
true

julia> Array{Float64, 3} <: VecOrMat{Float64}
false
```
