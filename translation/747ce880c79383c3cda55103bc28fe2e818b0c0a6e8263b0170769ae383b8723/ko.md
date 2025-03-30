```
chomp(s::AbstractString) -> SubString
```

문자열에서 단일 후행 개행 문자를 제거합니다.

자세한 내용은 [`chop`](@ref)를 참조하세요.

# 예제

```jldoctest
julia> chomp("Hello\n")
"Hello"
```
