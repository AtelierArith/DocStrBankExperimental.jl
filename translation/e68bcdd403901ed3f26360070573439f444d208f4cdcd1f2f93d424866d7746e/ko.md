```
complex(r, [i])
```

실수 또는 배열을 복소수로 변환합니다. `i`는 기본값이 0입니다.

# 예제

```jldoctest
julia> complex(7)
7 + 0im

julia> complex([1, 2, 3])
3-element Vector{Complex{Int64}}:
 1 + 0im
 2 + 0im
 3 + 0im
```
