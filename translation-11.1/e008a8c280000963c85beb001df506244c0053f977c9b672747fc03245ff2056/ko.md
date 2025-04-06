```
indexin(a, b)
```

`b`의 각 값에 대해 `a`의 첫 번째 인덱스를 포함하는 배열을 반환합니다. 출력 배열은 `a`가 `b`의 구성원이 아닐 경우 `nothing`을 포함합니다.

참고: [`sortperm`](@ref), [`findfirst`](@ref).

# 예제

```jldoctest
julia> a = ['a', 'b', 'c', 'b', 'd', 'a'];

julia> b = ['a', 'b', 'c'];

julia> indexin(a, b)
6-element Vector{Union{Nothing, Int64}}:
 1
 2
 3
 2
  nothing
 1

julia> indexin(b, a)
3-element Vector{Union{Nothing, Int64}}:
 1
 2
 3
```
