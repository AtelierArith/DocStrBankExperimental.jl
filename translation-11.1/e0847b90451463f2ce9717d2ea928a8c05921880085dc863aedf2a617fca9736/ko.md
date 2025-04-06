```
ismutable(v) -> Bool
```

값 `v`가 변경 가능하면 `true`를 반환합니다. 불변성에 대한 논의는 [Mutable Composite Types](@ref)를 참조하십시오. 이 함수는 값에 대해 작동하므로, `DataType`을 제공하면 해당 유형의 값이 변경 가능하다고 알려줍니다.

!!! note
    기술적인 이유로, `ismutable`은 특정 특수 유형(예: `String` 및 `Symbol`)의 값에 대해 `true`를 반환하지만, 이들은 허용 가능한 방식으로 변경될 수 없습니다.


또한 [`isbits`](@ref), [`isstructtype`](@ref)를 참조하십시오.

# 예제

```jldoctest
julia> ismutable(1)
false

julia> ismutable([1,2])
true
```

!!! compat "Julia 1.5"
    이 함수는 최소한 Julia 1.5가 필요합니다.

