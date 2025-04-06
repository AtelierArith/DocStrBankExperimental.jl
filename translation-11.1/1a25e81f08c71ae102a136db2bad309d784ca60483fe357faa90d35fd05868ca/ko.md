```
startswith(s::AbstractString, prefix::Regex)
```

`prefix` 정규 표현식 패턴으로 `s`가 시작하면 `true`를 반환합니다.

!!! note
    `startswith`는 앵커링을 정규 표현식에 컴파일하지 않고, 대신 앵커링을 `match_option`으로 PCRE에 전달합니다. 컴파일 시간이 분산되는 경우, `occursin(r"^...", s)`는 `startswith(s, r"...")`보다 빠릅니다.


또한 [`occursin`](@ref) 및 [`endswith`](@ref)를 참조하십시오.

!!! compat "Julia 1.2"
    이 메서드는 최소한 Julia 1.2가 필요합니다.


# 예제

```jldoctest
julia> startswith("JuliaLang", r"Julia|Romeo")
true
```
