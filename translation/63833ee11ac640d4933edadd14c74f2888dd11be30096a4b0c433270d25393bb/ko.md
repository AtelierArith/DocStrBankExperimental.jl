```
^(s::Union{AbstractString,AbstractChar}, n::Integer) -> AbstractString
```

문자열 또는 문자를 `n` 번 반복합니다. 이것은 `repeat(s, n)`으로도 작성할 수 있습니다.

자세한 내용은 [`repeat`](@ref)를 참조하세요.

# 예제

```jldoctest
julia> "Test "^3
"Test Test Test "
```
