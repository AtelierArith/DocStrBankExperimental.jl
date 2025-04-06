```
chopprefix(s::AbstractString, prefix::Union{AbstractString,Regex}) -> SubString
```

`s`에서 접두사 `prefix`를 제거합니다. 만약 `s`가 `prefix`로 시작하지 않으면, `s`와 동일한 문자열이 반환됩니다.

자세한 내용은 [`chopsuffix`](@ref)를 참조하세요.

!!! compat "Julia 1.8"
    이 함수는 Julia 1.8부터 사용할 수 있습니다.


# 예제

```jldoctest
julia> chopprefix("Hamburger", "Ham")
"burger"

julia> chopprefix("Hamburger", "hotdog")
"Hamburger"
```
