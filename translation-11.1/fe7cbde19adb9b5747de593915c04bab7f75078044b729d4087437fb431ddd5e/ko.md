```
VecOrMat{T}
```

[`Vector{T}`](@ref)와 [`Matrix{T}`](@ref)의 유니온 타입으로, 함수가 행렬 또는 벡터를 모두 수용할 수 있도록 합니다.

# 예제

```jldoctest
julia> Vector{Float64} <: VecOrMat{Float64}
true

julia> Matrix{Float64} <: VecOrMat{Float64}
true

julia> Array{Float64, 3} <: VecOrMat{Float64}
false
```
