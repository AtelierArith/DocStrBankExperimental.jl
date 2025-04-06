```
deleteat!(a::Vector, i::Integer)
```

주어진 `i`에서 항목을 제거하고 수정된 `a`를 반환합니다. 이후 항목들은 결과적으로 생긴 간격을 메우기 위해 이동됩니다.

참고: [`keepat!`](@ref), [`delete!`](@ref), [`popat!`](@ref), [`splice!`](@ref).

# 예제

```jldoctest
julia> deleteat!([6, 5, 4, 3, 2, 1], 2)
5-element Vector{Int64}:
 6
 4
 3
 2
 1
```
