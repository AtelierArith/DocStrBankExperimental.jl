```
leading_ones(x::Integer) -> Integer
```

`x`의 이진 표현에서 앞에 있는 1의 개수입니다.

# 예시

```jldoctest
julia> leading_ones(UInt32(2 ^ 32 - 2))
31
```
