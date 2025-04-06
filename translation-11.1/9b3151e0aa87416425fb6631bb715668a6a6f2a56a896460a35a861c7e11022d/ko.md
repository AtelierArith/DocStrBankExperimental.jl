```
trunc(dt::TimeType, ::Type{Period}) -> TimeType
```

주어진 `Period` 유형에 따라 `dt`의 값을 잘라냅니다.

# 예제

```jldoctest
julia> trunc(DateTime("1996-01-01T12:30:00"), Day)
1996-01-01T00:00:00
```
