```
thisind(s::AbstractString, i::Integer) -> Int
```

`s`에서 `i`가 유효한 범위에 있으면, `i`가 포함된 문자 인코딩 코드 유닛의 시작 인덱스를 반환합니다. 다시 말해, `i`가 문자의 시작이면 `i`를 반환하고, `i`가 문자의 시작이 아니면 문자의 시작까지 되돌아가서 해당 인덱스를 반환합니다. `i`가 0 또는 `ncodeunits(s)+1`과 같으면 `i`를 반환합니다. 그 외의 경우에는 `BoundsError`를 발생시킵니다.

# 예제

```jldoctest
julia> thisind("α", 0)
0

julia> thisind("α", 1)
1

julia> thisind("α", 2)
1

julia> thisind("α", 3)
3

julia> thisind("α", 4)
ERROR: BoundsError: attempt to access 2-codeunit String at index [4]
[...]

julia> thisind("α", -1)
ERROR: BoundsError: attempt to access 2-codeunit String at index [-1]
[...]
```
