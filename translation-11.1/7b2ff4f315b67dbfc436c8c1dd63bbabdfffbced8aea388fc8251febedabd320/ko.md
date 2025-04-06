```
week(dt::TimeType) -> Int64
```

`Date` 또는 `DateTime`의 [ISO 주 날짜](https://en.wikipedia.org/wiki/ISO_week_date)를 [`Int64`](@ref)로 반환합니다. 연도의 첫 번째 주는 연도의 첫 번째 목요일이 포함된 주이며, 이로 인해 1월 4일 이전의 날짜가 이전 연도의 마지막 주에 포함될 수 있습니다. 예를 들어, `week(Date(2005, 1, 1))`은 2004년의 53번째 주입니다.

# 예시

```jldoctest
julia> week(Date(1989, 6, 22))
25

julia> week(Date(2005, 1, 1))
53

julia> week(Date(2004, 12, 31))
53
```
