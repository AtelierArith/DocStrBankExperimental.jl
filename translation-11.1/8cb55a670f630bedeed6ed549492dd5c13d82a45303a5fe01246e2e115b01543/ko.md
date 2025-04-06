```
count_ones(x::Integer) -> Integer
```

`x`의 이진 표현에서 1의 개수.

# 예시

```jldoctest
julia> count_ones(7)
3

julia> count_ones(Int32(-1))
32
```
