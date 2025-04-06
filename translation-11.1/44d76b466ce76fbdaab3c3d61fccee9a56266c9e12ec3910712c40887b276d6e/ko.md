```
isvalid(s::AbstractString, i::Integer) -> Bool
```

주어진 인덱스가 `s`에서 문자의 인코딩 시작인지 여부를 나타내는 술어입니다. `isvalid(s, i)`가 true이면 `s[i]`는 해당 인덱스에서 인코딩이 시작되는 문자를 반환하고, false이면 `s[i]`는 유효하지 않은 인덱스 오류 또는 `i`가 범위 내에 있는지에 따라 경계 오류를 발생시킵니다. `isvalid(s, i)`가 O(1) 함수가 되기 위해서는 `s`의 인코딩이 [자기 동기화](https://en.wikipedia.org/wiki/Self-synchronizing_code)되어야 합니다. 이는 Julia의 일반 문자열 지원에 대한 기본 가정입니다.

또한 [`getindex`](@ref), [`iterate`](@ref), [`thisind`](@ref), [`nextind`](@ref), [`prevind`](@ref), [`length`](@ref)를 참조하십시오.

# 예제

```jldoctest
julia> str = "αβγdef";

julia> isvalid(str, 1)
true

julia> str[1]
'α': Unicode U+03B1 (category Ll: Letter, lowercase)

julia> isvalid(str, 2)
false

julia> str[2]
ERROR: StringIndexError: invalid index [2], valid nearby indices [1]=>'α', [3]=>'β'
Stacktrace:
[...]
```
