```
last(itr, n::Integer)
```

iterable 컬렉션 `itr`의 마지막 `n` 요소를 가져오거나, `itr`가 충분히 길지 않은 경우 더 적은 요소를 가져옵니다.

!!! compat "Julia 1.6"
    이 메서드는 최소한 Julia 1.6이 필요합니다.


# 예제

```jldoctest
julia> last(["foo", "bar", "qux"], 2)
2-element Vector{String}:
 "bar"
 "qux"

julia> last(1:6, 10)
1:6

julia> last(Float64[], 1)
Float64[]
```
