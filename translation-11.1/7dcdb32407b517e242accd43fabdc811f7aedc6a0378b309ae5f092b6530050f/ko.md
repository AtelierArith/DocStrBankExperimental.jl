```
escape_string(str::AbstractString[, esc]; keep = ())::AbstractString
escape_string(io, str::AbstractString[, esc]; keep = ())::Nothing
```

전통적인 C 및 유니코드 이스케이프 시퀀스의 일반적인 이스케이프. 첫 번째 형식은 이스케이프된 문자열을 반환하고, 두 번째는 결과를 `io`에 출력합니다.

백슬래시(`\`)는 이중 백슬래시(`"\\"`)로 이스케이프됩니다. 비인쇄 가능한 문자는 표준 C 이스케이프 코드, NUL에 대한 `"\0"`(모호하지 않은 경우), 유니코드 코드 포인트(`"\u"` 접두사) 또는 16진수(`"\x"` 접두사)로 이스케이프됩니다.

선택적 `esc` 인수는 백슬래시로 이스케이프되어야 하는 추가 문자를 지정합니다(`"`는 첫 번째 형식에서 기본적으로 이스케이프됩니다).

인수 `keep`는 있는 그대로 유지되어야 하는 문자 집합을 지정합니다. 여기서 `esc`가 우선합니다.

역작업에 대한 [`unescape_string`](@ref)도 참조하십시오.

!!! compat "Julia 1.7"
    `keep` 인수는 Julia 1.7부터 사용할 수 있습니다.


# 예제

```jldoctest
julia> escape_string("aaa\nbbb")
"aaa\\nbbb"

julia> escape_string("aaa\nbbb"; keep = '\n')
"aaa\nbbb"

julia> escape_string("\xfe\xff") # 유효하지 않은 utf-8
"\\xfe\\xff"

julia> escape_string(string('\u2135','\0')) # 모호하지 않음
"ℵ\\0"

julia> escape_string(string('\u2135','\0','0')) # \0는 모호할 수 있음
"ℵ\\x000"
```
