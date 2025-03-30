```
sort(A; dims::Integer, alg::Algorithm=defalg(A), lt=isless, by=identity, rev::Bool=false, order::Ordering=Forward)
```

주어진 차원에 따라 다차원 배열 `A`를 정렬합니다. 가능한 키워드 인수에 대한 설명은 [`sort!`](@ref)를 참조하십시오.

배열의 슬라이스를 정렬하려면 [`sortslices`](@ref)를 참조하십시오.

# 예제

```jldoctest
julia> A = [4 3; 1 2]
2×2 Matrix{Int64}:
 4  3
 1  2

julia> sort(A, dims = 1)
2×2 Matrix{Int64}:
 1  2
 4  3

julia> sort(A, dims = 2)
2×2 Matrix{Int64}:
 3  4
 1  2
```
