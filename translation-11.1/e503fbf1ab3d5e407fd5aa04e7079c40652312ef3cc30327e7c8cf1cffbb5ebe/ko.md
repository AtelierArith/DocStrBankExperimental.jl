```
cross(x, y)
×(x,y)
```

두 3-벡터의 외적을 계산합니다.

# 예제

```jldoctest
julia> a = [0;1;0]
3-element Vector{Int64}:
 0
 1
 0

julia> b = [0;0;1]
3-element Vector{Int64}:
 0
 0
 1

julia> cross(a,b)
3-element Vector{Int64}:
 1
 0
 0
```
