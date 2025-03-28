```
VecOrMat{T}
```

Union-Typ von [`Vector{T}`](@ref) und [`Matrix{T}`](@ref), der es Funktionen ermöglicht, entweder eine Matrix oder einen Vektor zu akzeptieren.

# Beispiele

```jldoctest
julia> Vector{Float64} <: VecOrMat{Float64}
true

julia> Matrix{Float64} <: VecOrMat{Float64}
true

julia> Array{Float64, 3} <: VecOrMat{Float64}
false
```
