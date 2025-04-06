```
startswith(s::AbstractString, prefix::Union{AbstractString,Base.Chars})
```

`s`가 `prefix`로 시작하면 `true`를 반환합니다. `prefix`는 문자열, 문자 또는 문자 튜플/벡터/집합일 수 있습니다. `prefix`가 문자 튜플/벡터/집합인 경우, `s`의 첫 번째 문자가 해당 집합에 속하는지 테스트합니다.

자세한 내용은 [`endswith`](@ref), [`contains`](@ref)를 참조하세요.

# 예제

```jldoctest
julia> startswith("JuliaLang", "Julia")
true
```
