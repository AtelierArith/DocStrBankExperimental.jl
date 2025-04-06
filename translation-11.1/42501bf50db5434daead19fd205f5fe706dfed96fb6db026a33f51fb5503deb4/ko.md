```
isimmutable(v) -> Bool
```

!!! warning
    `isimmutable(v)`는 향후 릴리스에서 `!ismutable(v)`로 대체될 예정이므로 대신 `!ismutable(v)`를 사용하는 것을 고려하세요. (Julia 1.5부터)


값 `v`가 불변이면 `true`를 반환합니다. 불변성에 대한 논의는 [Mutable Composite Types](@ref)를 참조하세요. 이 함수는 값에 대해 작동하므로, 타입을 제공하면 `DataType`의 값이 가변적이라고 알려줍니다.

# 예제

```jldoctest
julia> isimmutable(1)
true

julia> isimmutable([1,2])
false
```
