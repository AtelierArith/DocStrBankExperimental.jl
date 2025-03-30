```
VecOrMat{T}
```

[`Vector{T}`](@ref) ve [`Matrix{T}`](@ref) union türü, fonksiyonların ya bir Matris ya da bir Vektör kabul etmesine olanak tanır.

# Örnekler

```jldoctest
julia> Vector{Float64} <: VecOrMat{Float64}
true

julia> Matrix{Float64} <: VecOrMat{Float64}
true

julia> Array{Float64, 3} <: VecOrMat{Float64}
false
```
