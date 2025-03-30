```
uppercase(c::AbstractChar)
```

`c`를 대문자로 변환합니다.

또한 [`lowercase`](@ref), [`titlecase`](@ref)를 참조하세요.

# 예제

```jldoctest
julia> uppercase('a')
'A': ASCII/Unicode U+0041 (category Lu: Letter, uppercase)

julia> uppercase('ê')
'Ê': Unicode U+00CA (category Lu: Letter, uppercase)
```
