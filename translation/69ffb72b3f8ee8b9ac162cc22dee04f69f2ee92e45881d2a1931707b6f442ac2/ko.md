```
dayofweek(dt::TimeType) -> Int64
```

주를 나타내는 [`Int64`](@ref)를 반환하며 `1 = 월요일, 2 = 화요일, 등.`입니다.

# 예시

```jldoctest
julia> dayofweek(Date("2000-01-01"))
6
```
