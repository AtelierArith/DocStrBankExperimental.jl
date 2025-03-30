```
Adjoint
```

기본 선형 대수 객체의 어드전트 뷰에 대한 지연 래퍼 유형으로, 일반적으로 `AbstractVector`/`AbstractMatrix`입니다. 일반적으로 `Adjoint` 생성자는 직접 호출하지 말고 대신 [`adjoint`](@ref)를 사용하십시오. 뷰를 구체화하려면 [`copy`](@ref)를 사용하십시오.

이 유형은 선형 대수 사용을 위해 설계되었습니다 - 일반 데이터 조작에 대해서는 [`permutedims`](@ref Base.permutedims)를 참조하십시오.

# 예제

```jldoctest
julia> A = [3+2im 9+2im; 0 0]
2×2 Matrix{Complex{Int64}}:
 3+2im  9+2im
 0+0im  0+0im

julia> Adjoint(A)
2×2 adjoint(::Matrix{Complex{Int64}}) with eltype Complex{Int64}:
 3-2im  0+0im
 9-2im  0+0im
```
