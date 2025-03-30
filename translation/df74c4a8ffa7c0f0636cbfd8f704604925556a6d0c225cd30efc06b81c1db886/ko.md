```
Dates.RFC1123Format
```

날짜와 시간에 대한 RFC1123 형식을 설명합니다.

# 예제

```jldoctest
julia> Dates.format(DateTime(2018, 8, 8, 12, 0, 43, 1), RFC1123Format)
"Wed, 08 Aug 2018 12:00:43"
```
