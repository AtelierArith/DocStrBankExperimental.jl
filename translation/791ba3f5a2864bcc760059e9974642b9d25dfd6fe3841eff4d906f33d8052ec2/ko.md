```
findfirst(pattern::AbstractString, string::AbstractString)
findfirst(pattern::AbstractPattern, string::String)
```

`string`에서 `pattern`의 첫 번째 발생을 찾습니다. [`findnext(pattern, string, firstindex(s))`](@ref)와 동등합니다.

# 예제

```jldoctest
julia> findfirst("z", "Hello to the world") # 아무것도 반환하지 않지만 REPL에 출력되지 않음

julia> findfirst("Julia", "JuliaLang")
1:5
```
