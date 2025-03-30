```
contains(haystack::AbstractString, needle)
```

`haystack`에 `needle`이 포함되어 있으면 `true`를 반환합니다. 이는 `occursin(needle, haystack)`와 동일하지만, `startswith(haystack, needle)` 및 `endswith(haystack, needle)`와의 일관성을 위해 제공됩니다.

또한 [`occursin`](@ref), [`in`](@ref), [`issubset`](@ref)를 참조하세요.

# 예제

```jldoctest
julia> contains("JuliaLang is pretty cool!", "Julia")
true

julia> contains("JuliaLang is pretty cool!", 'a')
true

julia> contains("aba", r"a.a")
true

julia> contains("abba", r"a.a")
false
```

!!! compat "Julia 1.5"
    `contains` 함수는 최소한 Julia 1.5가 필요합니다.

