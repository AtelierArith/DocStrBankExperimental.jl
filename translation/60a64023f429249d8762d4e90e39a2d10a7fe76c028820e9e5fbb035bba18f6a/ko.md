```
titlecase(c::AbstractChar)
```

`c`를 제목 대문자로 변환합니다. 이는 이중 자음의 경우 대문자와 다를 수 있으므로 아래 예제를 비교하십시오.

자세한 내용은 [`uppercase`](@ref), [`lowercase`](@ref)를 참조하십시오.

# 예제

```jldoctest
julia> titlecase('a')
'A': ASCII/Unicode U+0041 (category Lu: Letter, uppercase)

julia> titlecase('ǆ')
'ǅ': Unicode U+01C5 (category Lt: Letter, titlecase)

julia> uppercase('ǆ')
'Ǆ': Unicode U+01C4 (category Lu: Letter, uppercase)
```
