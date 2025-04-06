```
copy(A::Transpose)
copy(A::Adjoint)
```

지연 행렬 전치/수반을 즉시 평가합니다. 전치는 요소에 재귀적으로 적용된다는 점에 유의하십시오.

이 작업은 선형 대수 사용을 위해 의도되었습니다 - 일반 데이터 조작에 대해서는 [`permutedims`](@ref Base.permutedims)를 참조하십시오. 이는 비재귀적입니다.

# 예제

```jldoctest
julia> A = [1 2im; -3im 4]
2×2 Matrix{Complex{Int64}}:
 1+0im  0+2im
 0-3im  4+0im

julia> T = transpose(A)
2×2 transpose(::Matrix{Complex{Int64}}) with eltype Complex{Int64}:
 1+0im  0-3im
 0+2im  4+0im

julia> copy(T)
2×2 Matrix{Complex{Int64}}:
 1+0im  0-3im
 0+2im  4+0im
```
