```
repeat(c::AbstractChar, r::Integer) -> String
```

문자를 `r` 번 반복합니다. 이는 [`c^r`](@ref :^(::Union{AbstractString, AbstractChar}, ::Integer))를 호출하여 동일하게 수행할 수 있습니다.

# 예제

```jldoctest
julia> repeat('A', 3)
"AAA"
```
