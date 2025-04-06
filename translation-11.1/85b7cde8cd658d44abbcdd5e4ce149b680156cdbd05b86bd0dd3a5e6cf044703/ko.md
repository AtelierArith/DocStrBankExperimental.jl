```
SubstitutionString(substr) <: AbstractString
```

주어진 문자열 `substr`을 `SubstitutionString`으로 저장하여 정규 표현식 치환에 사용합니다. 가장 일반적으로 [`@s_str`](@ref) 매크로를 사용하여 생성됩니다.

# 예제

```jldoctest
julia> SubstitutionString("Hello \\g<name>, it's \\1")
s"Hello \g<name>, it's \1"

julia> subst = s"Hello \g<name>, it's \1"
s"Hello \g<name>, it's \1"

julia> typeof(subst)
SubstitutionString{String}
```
