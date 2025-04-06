```
chopsuffix(s::AbstractString, suffix::Union{AbstractString,Regex}) -> SubString
```

`s`에서 접미사 `suffix`를 제거합니다. 만약 `s`가 `suffix`로 끝나지 않으면, `s`와 동일한 문자열이 반환됩니다.

자세한 내용은 [`chopprefix`](@ref)를 참조하세요.

!!! compat "Julia 1.8"
    이 함수는 Julia 1.8부터 사용할 수 있습니다.


# 예제

```jldoctest
julia> chopsuffix("Hamburger", "er")
"Hamburg"

julia> chopsuffix("Hamburger", "hotdog")
"Hamburger"
```
