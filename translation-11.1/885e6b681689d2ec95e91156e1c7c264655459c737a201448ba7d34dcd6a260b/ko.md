```
DateTime(dt::AbstractString, df::DateFormat=ISODateTimeFormat) -> DateTime
```

`dt` 날짜 시간 문자열을 [`DateFormat`](@ref) 객체에 주어진 패턴에 따라 파싱하여 `DateTime`을 생성합니다. 생략할 경우 날짜 형식은 "yyyy-mm-dd\THH:MM:SS.s"입니다.

`DateTime(::AbstractString, ::AbstractString)`와 유사하지만, 미리 생성된 `DateFormat` 객체를 사용하여 유사한 형식의 날짜 시간 문자열을 반복적으로 파싱할 때 더 효율적입니다.
