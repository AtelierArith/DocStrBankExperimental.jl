```
keys(m::RegexMatch) -> Vector
```

모든 캡처 그룹에 대한 키의 벡터를 반환합니다. 키는 캡처 그룹이 일치하지 않더라도 포함됩니다. 즉, `idx`는 `m[idx] == nothing`인 경우에도 반환 값에 포함됩니다.

이름이 없는 캡처 그룹은 해당 인덱스에 해당하는 정수 키를 가집니다. 이름이 있는 캡처 그룹은 문자열 키를 가집니다.

!!! compat "Julia 1.7"
    이 메서드는 Julia 1.7에 추가되었습니다.


# 예제

```jldoctest
julia> keys(match(r"(?<hour>\d+):(?<minute>\d+)(am|pm)?", "11:30"))
3-element Vector{Any}:
  "hour"
  "minute"
 3
```
