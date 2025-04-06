```
UnitLowerTriangular(A::AbstractMatrix)
```

행렬 `A`의 `UnitLowerTriangular` 뷰를 생성합니다. 이러한 뷰는 `A`의 [`eltype`](@ref)의 [`oneunit`](@ref)을 대각선에 가집니다.

# 예제

```jldoctest
julia> A = [1.0 2.0 3.0; 4.0 5.0 6.0; 7.0 8.0 9.0]
3×3 Matrix{Float64}:
 1.0  2.0  3.0
 4.0  5.0  6.0
 7.0  8.0  9.0

julia> UnitLowerTriangular(A)
3×3 UnitLowerTriangular{Float64, Matrix{Float64}}:
 1.0   ⋅    ⋅
 4.0  1.0   ⋅
 7.0  8.0  1.0
```
