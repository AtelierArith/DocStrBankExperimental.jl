```
endswith(s::AbstractString, suffix::Regex)
```

`s`가 정규 표현식 패턴 `suffix`로 끝나면 `true`를 반환합니다.

!!! note
    `endswith`는 앵커링을 정규 표현식으로 컴파일하지 않고, 대신 앵커링을 `match_option`으로 PCRE에 전달합니다. 컴파일 시간이 분산되는 경우, `occursin(r"...$", s)`는 `endswith(s, r"...")`보다 빠릅니다.


또한 [`occursin`](@ref) 및 [`startswith`](@ref)를 참조하십시오.

!!! compat "Julia 1.2"
    이 메서드는 최소한 Julia 1.2가 필요합니다.


# 예제

```jldoctest
julia> endswith("JuliaLang", r"Lang|Roberts")
true
```
