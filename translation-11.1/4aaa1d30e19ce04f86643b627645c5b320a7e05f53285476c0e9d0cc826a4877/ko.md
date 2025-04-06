```
Time(t::AbstractString, df::DateFormat=ISOTimeFormat) -> Time
```

주어진 [`DateFormat`](@ref) 객체의 패턴에 따라 `t` 날짜 시간 문자열을 파싱하여 `Time`을 생성합니다. 생략할 경우 dateformat"HH:MM:SS.s"를 사용합니다.

`Time(::AbstractString, ::AbstractString)`와 유사하지만, 미리 생성된 `DateFormat` 객체를 사용하여 유사한 형식의 시간 문자열을 반복적으로 파싱할 때 더 효율적입니다.
