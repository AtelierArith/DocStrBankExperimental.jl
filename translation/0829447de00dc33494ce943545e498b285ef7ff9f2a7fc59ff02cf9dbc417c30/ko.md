```
sort!(A; dims::Integer, alg::Algorithm=defalg(A), lt=isless, by=identity, rev::Bool=false, order::Ordering=Forward)
```

다차원 배열 `A`를 차원 `dims`에 따라 정렬합니다. 가능한 키워드 인수에 대한 설명은 [`sort!`](@ref)의 일차원 버전을 참조하십시오.

배열의 슬라이스를 정렬하려면 [`sortslices`](@ref)를 참조하십시오.

!!! compat "Julia 1.1"
    이 함수는 최소한 Julia 1.1이 필요합니다.


# 예제

```jldoctest
julia> A = [4 3; 1 2]
2×2 Matrix{Int64}:
 4  3
 1  2

julia> sort!(A, dims = 1); A
2×2 Matrix{Int64}:
 1  2
 4  3

julia> sort!(A, dims = 2); A
2×2 Matrix{Int64}:
 1  2
 3  4
```
