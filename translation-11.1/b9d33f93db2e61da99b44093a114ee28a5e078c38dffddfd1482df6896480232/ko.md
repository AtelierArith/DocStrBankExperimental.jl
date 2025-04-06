```
Unicode.isassigned(c) -> Bool
```

주어진 문자 또는 정수가 할당된 유니코드 코드 포인트인 경우 `true`를 반환합니다.

# 예시

```jldoctest
julia> Unicode.isassigned(101)
true

julia> Unicode.isassigned('\x01')
true
```
