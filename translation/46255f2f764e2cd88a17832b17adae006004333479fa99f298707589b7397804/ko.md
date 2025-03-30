```
eachcol(A::AbstractVecOrMat) <: AbstractVector
```

[`ColumnSlices`](@ref) 객체를 생성하여 행렬 또는 벡터 `A`의 열 벡터를 만듭니다. 열 슬라이스는 `A`의 `AbstractVector` 뷰로 반환됩니다.

반대의 경우는 [`stack`](@ref)`(cols)` 또는 `reduce(`[`hcat`](@ref)`, cols)`를 참조하세요.

또한 [`eachrow`](@ref), [`eachslice`](@ref) 및 [`mapslices`](@ref)도 참조하세요.

!!! compat "Julia 1.1"
    이 함수는 최소한 Julia 1.1이 필요합니다.


!!! compat "Julia 1.9"
    Julia 1.9 이전에는 이 함수가 이터레이터를 반환했습니다.


# 예제

```jldoctest
julia> a = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> s = eachcol(a)
2-element ColumnSlices{Matrix{Int64}, Tuple{Base.OneTo{Int64}}, SubArray{Int64, 1, Matrix{Int64}, Tuple{Base.Slice{Base.OneTo{Int64}}, Int64}, true}}:
 [1, 3]
 [2, 4]

julia> s[1]
2-element view(::Matrix{Int64}, :, 1) with eltype Int64:
 1
 3
```
