```
nullspace(M; atol::Real=0, rtol::Real=atol>0 ? 0 : n*ϵ)
nullspace(M, rtol::Real) = nullspace(M; rtol=rtol) # to be deprecated in Julia 2.0
```

`M`의 널 공간에 대한 기저를 계산합니다. 여기서 `M`의 특이값 중 크기가 `max(atol, rtol*σ₁)`보다 작은 특이 벡터를 포함합니다. 여기서 `σ₁`은 `M`의 가장 큰 특이값입니다.

기본적으로 상대 허용 오차 `rtol`은 `n*ϵ`이며, 여기서 `n`은 `M`의 가장 작은 차원의 크기이고, `ϵ`은 `M`의 요소 유형의 [`eps`](@ref)입니다.

# 예제

```jldoctest
julia> M = [1 0 0; 0 1 0; 0 0 0]
3×3 Matrix{Int64}:
 1  0  0
 0  1  0
 0  0  0

julia> nullspace(M)
3×1 Matrix{Float64}:
 0.0
 0.0
 1.0

julia> nullspace(M, rtol=3)
3×3 Matrix{Float64}:
 0.0  1.0  0.0
 1.0  0.0  0.0
 0.0  0.0  1.0

julia> nullspace(M, atol=0.95)
3×1 Matrix{Float64}:
 0.0
 0.0
 1.0
```
