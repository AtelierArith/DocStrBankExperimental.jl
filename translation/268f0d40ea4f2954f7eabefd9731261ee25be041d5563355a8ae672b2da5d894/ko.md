```
전치
```

기본 선형 대수 객체의 전치 뷰에 대한 게으른 래퍼 유형으로, 일반적으로 `AbstractVector`/`AbstractMatrix`입니다. 일반적으로 `Transpose` 생성자는 직접 호출하지 말고 대신 [`transpose`](@ref)를 사용하십시오. 뷰를 구체화하려면 [`copy`](@ref)를 사용하십시오.

이 유형은 선형 대수 사용을 위해 설계되었습니다 - 일반 데이터 조작에 대해서는 [`permutedims`](@ref Base.permutedims)를 참조하십시오.

# 예제

```jldoctest
julia> A = [2 3; 0 0]
2×2 Matrix{Int64}:
 2  3
 0  0

julia> Transpose(A)
2×2 transpose(::Matrix{Int64}) with eltype Int64:
 2  0
 3  0
```
