```
count_zeros(x::Integer) -> Integer
```

`x`의 이진 표현에서 0의 개수.

# 예시

```jldoctest
julia> count_zeros(Int32(2 ^ 16 - 1))
16

julia> count_zeros(-1)
0
```
