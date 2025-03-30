```
endswith(s::AbstractString, suffix::Union{AbstractString,Base.Chars})
```

`s`가 `suffix`로 끝나면 `true`를 반환합니다. `suffix`는 문자열, 문자 또는 문자 튜플/벡터/집합일 수 있습니다. `suffix`가 문자 튜플/벡터/집합인 경우, `s`의 마지막 문자가 해당 집합에 속하는지 테스트합니다.

또한 [`startswith`](@ref), [`contains`](@ref)를 참조하세요.

# 예제

```jldoctest
julia> endswith("Sunday", "day")
true
```
