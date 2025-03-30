```
isperm(v) -> Bool
```

`v`가 유효한 순열이면 `true`를 반환합니다.

# 예시

```jldoctest
julia> isperm([1; 2])
true

julia> isperm([1; 3])
false
```
