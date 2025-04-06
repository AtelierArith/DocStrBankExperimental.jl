```
occursin(haystack)
```

`haystack`에서 인수가 발생하는지 확인하는 함수를 만듭니다. 즉, `needle -> occursin(needle, haystack)`와 동등한 함수입니다.

반환된 함수는 `Base.Fix2{typeof(occursin)}` 유형입니다.

!!! compat "Julia 1.6"
    이 메서드는 Julia 1.6 이상이 필요합니다.


# 예제

```jldoctest
julia> search_f = occursin("JuliaLang is a programming language");

julia> search_f("JuliaLang")
true

julia> search_f("Python")
false
```
