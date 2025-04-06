```
Diagonal(V::AbstractVector)
```

`V`를 대각선으로 하는 지연 행렬을 생성합니다.

지연 단위 행렬 `I`에 대한 [`UniformScaling`](@ref), 조밀한 행렬을 만들기 위한 [`diagm`](@ref), 대각선 요소를 추출하기 위한 [`diag`](@ref)도 참조하세요.

# 예제

```jldoctest
julia> d = Diagonal([1, 10, 100])
3×3 Diagonal{Int64, Vector{Int64}}:
 1   ⋅    ⋅
 ⋅  10    ⋅
 ⋅   ⋅  100

julia> diagm([7, 13])
2×2 Matrix{Int64}:
 7   0
 0  13

julia> ans + I
2×2 Matrix{Int64}:
 8   0
 0  14

julia> I(2)
2×2 Diagonal{Bool, Vector{Bool}}:
 1  ⋅
 ⋅  1
```

!!! note
    한 열 행렬은 벡터처럼 처리되지 않고, 대신 1-요소 `diag(A)`를 추출하는 `Diagonal(A::AbstractMatrix)` 메서드를 호출합니다:


```jldoctest
julia> A = transpose([7.0 13.0])
2×1 transpose(::Matrix{Float64}) with eltype Float64:
  7.0
 13.0

julia> Diagonal(A)
1×1 Diagonal{Float64, Vector{Float64}}:
 7.0
```
