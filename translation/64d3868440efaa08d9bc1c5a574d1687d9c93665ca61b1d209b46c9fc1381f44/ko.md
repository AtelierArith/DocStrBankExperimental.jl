```
isleapyear(dt::TimeType) -> Bool
```

`dt`의 연도가 윤년이면 `true`를 반환합니다.

# 예제

```jldoctest
julia> isleapyear(Date("2004"))
true

julia> isleapyear(Date("2005"))
false
```
