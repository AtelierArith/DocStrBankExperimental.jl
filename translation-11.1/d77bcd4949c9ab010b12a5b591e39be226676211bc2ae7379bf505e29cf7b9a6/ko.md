```
repeat(s::AbstractString, r::Integer)
```

문자열을 `r` 번 반복합니다. 이는 `s^r`로 작성할 수 있습니다.

자세한 내용은 [`^`](@ref :^(::Union{AbstractString, AbstractChar}, ::Integer))를 참조하세요.

# 예제

```jldoctest
julia> repeat("ha", 3)
"hahaha"
```
