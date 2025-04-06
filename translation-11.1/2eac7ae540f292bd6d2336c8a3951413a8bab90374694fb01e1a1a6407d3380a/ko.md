```
occursin(needle::Union{AbstractString,AbstractPattern,AbstractChar}, haystack::AbstractString)
```

두 번째 인수의 부분 문자열인지 첫 번째 인수를 확인합니다. `needle`이 정규 표현식인 경우, `haystack`에 일치하는 항목이 있는지 확인합니다.

# 예제

```jldoctest
julia> occursin("Julia", "JuliaLang is pretty cool!")
true

julia> occursin('a', "JuliaLang is pretty cool!")
true

julia> occursin(r"a.a", "aba")
true

julia> occursin(r"a.a", "abba")
false
```

또한 [`contains`](@ref)를 참조하십시오.
