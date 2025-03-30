```
findlast(pattern::AbstractString, string::AbstractString)
```

`string`에서 `pattern`의 마지막 발생을 찾습니다. [`findprev(pattern, string, lastindex(string))`](@ref)와 동일합니다.

# 예제

```jldoctest
julia> findlast("o", "Hello to the world")
15:15

julia> findfirst("Julia", "JuliaLang")
1:5
```
