```
lowercase(c::AbstractChar)
```

`c`를 소문자로 변환합니다.

자세한 내용은 [`uppercase`](@ref), [`titlecase`](@ref)를 참조하세요.

# 예제

```jldoctest
julia> lowercase('A')
'a': ASCII/Unicode U+0061 (category Ll: Letter, lowercase)

julia> lowercase('Ö')
'ö': Unicode U+00F6 (category Ll: Letter, lowercase)
```
