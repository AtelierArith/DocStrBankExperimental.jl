```
selectdim(A, d::Integer, i)
```

`d` 차원의 인덱스가 `i`인 `A`의 모든 데이터의 뷰를 반환합니다.

`i`가 `d` 위치에 있는 `view(A,:,:,...,i,:,:,...)`와 동등합니다.

참고: [`eachslice`](@ref).

# 예제

```jldoctest
julia> A = [1 2 3 4; 5 6 7 8]
2×4 Matrix{Int64}:
 1  2  3  4
 5  6  7  8

julia> selectdim(A, 2, 3)
2-element view(::Matrix{Int64}, :, 3) with eltype Int64:
 3
 7

julia> selectdim(A, 2, 3:4)
2×2 view(::Matrix{Int64}, :, 3:4) with eltype Int64:
 3  4
 7  8
```
