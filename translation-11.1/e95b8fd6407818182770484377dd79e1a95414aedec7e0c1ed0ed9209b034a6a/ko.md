```
eps(::Type{DateTime}) -> 밀리초
eps(::Type{Date}) -> 일
eps(::Type{Time}) -> 나노초
eps(::TimeType) -> 기간
```

`TimeType`에서 지원하는 가장 작은 단위 값을 반환합니다.

# 예제

```jldoctest
julia> eps(DateTime)
1 밀리초

julia> eps(Date)
1 일

julia> eps(Time)
1 나노초
```
