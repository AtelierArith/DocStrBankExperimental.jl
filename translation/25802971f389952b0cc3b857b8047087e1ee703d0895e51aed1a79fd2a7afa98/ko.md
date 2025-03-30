```
nonmissingtype(T::Type)
```

`T`가 `Missing`을 포함하는 타입의 유니온인 경우, `Missing`이 제거된 새로운 타입을 반환합니다.

# 예시

```jldoctest
julia> nonmissingtype(Union{Int64,Missing})
Int64

julia> nonmissingtype(Any)
Any
```

!!! compat "Julia 1.3"
    이 함수는 Julia 1.3부터 내보내집니다.

