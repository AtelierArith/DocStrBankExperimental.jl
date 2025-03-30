```
ascii(s::AbstractString)
```

문자열을 `String` 유형으로 변환하고 ASCII 데이터만 포함되어 있는지 확인합니다. 그렇지 않은 경우 첫 번째 비ASCII 바이트의 위치를 나타내는 `ArgumentError`를 발생시킵니다.

비ASCII 문자를 필터링하거나 교체하기 위한 [`isascii`](@ref) 술어도 참조하십시오.

# 예제

```jldoctest
julia> ascii("abcdeγfgh")
ERROR: ArgumentError: invalid ASCII at index 6 in "abcdeγfgh"
Stacktrace:
[...]

julia> ascii("abcdefgh")
"abcdefgh"
```
