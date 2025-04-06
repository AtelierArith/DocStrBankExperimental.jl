```
insert!(a::Vector, index::Integer, item)
```

주어진 `index`에 `item`을 `a`에 삽입합니다. `index`는 결과적으로 `a`에서 `item`의 인덱스입니다.

참고: [`push!`](@ref), [`replace`](@ref), [`popat!`](@ref), [`splice!`](@ref).

# 예제

```jldoctest
julia> insert!(Any[1:6;], 3, "here")
7-element Vector{Any}:
 1
 2
  "here"
 3
 4
 5
 6
```
