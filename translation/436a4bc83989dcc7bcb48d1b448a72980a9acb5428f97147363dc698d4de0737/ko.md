```
eachslice(A::AbstractArray; dims, drop=true)
```

[`Slices`](@ref) 객체를 생성하여 `A`의 `dims` 차원에 대한 슬라이스 배열을 만들고, `A`의 다른 차원에서 모든 데이터를 선택하는 뷰를 반환합니다. `dims`는 정수 또는 정수의 튜플일 수 있습니다.

`drop = true`(기본값)인 경우, 외부 `Slices`는 내부 차원을 제거하고, 차원의 순서는 `dims`에 있는 순서와 일치합니다. `drop = false`인 경우, `Slices`는 기본 배열과 동일한 차원 수를 가지며, 내부 차원의 크기는 1입니다.

`eachslice(A; dims::Integer)`의 역인 [`stack`](@ref)`(slices; dims)`를 참조하세요.

또한 [`eachrow`](@ref), [`eachcol`](@ref), [`mapslices`](@ref) 및 [`selectdim`](@ref)도 참조하세요.

!!! compat "Julia 1.1"
    이 함수는 최소한 Julia 1.1이 필요합니다.


!!! compat "Julia 1.9"
    Julia 1.9 이전에는 이 함수가 이터레이터를 반환했으며, 단일 차원 `dims`만 지원되었습니다.


# 예제

```jldoctest
julia> m = [1 2 3; 4 5 6; 7 8 9]
3×3 Matrix{Int64}:
 1  2  3
 4  5  6
 7  8  9

julia> s = eachslice(m, dims=1)
3-element RowSlices{Matrix{Int64}, Tuple{Base.OneTo{Int64}}, SubArray{Int64, 1, Matrix{Int64}, Tuple{Int64, Base.Slice{Base.OneTo{Int64}}}, true}}:
 [1, 2, 3]
 [4, 5, 6]
 [7, 8, 9]

julia> s[1]
3-element view(::Matrix{Int64}, 1, :) with eltype Int64:
 1
 2
 3

julia> eachslice(m, dims=1, drop=false)
3×1 Slices{Matrix{Int64}, Tuple{Int64, Colon}, Tuple{Base.OneTo{Int64}, Base.OneTo{Int64}}, SubArray{Int64, 1, Matrix{Int64}, Tuple{Int64, Base.Slice{Base.OneTo{Int64}}}, true}, 2}:
 [1, 2, 3]
 [4, 5, 6]
 [7, 8, 9]
```
