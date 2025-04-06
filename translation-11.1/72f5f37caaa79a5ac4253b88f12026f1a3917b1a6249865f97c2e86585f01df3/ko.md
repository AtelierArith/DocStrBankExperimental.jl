```
StepRange{T, S} <: OrdinalRange{T, S}
```

타입 `T`의 요소와 타입 `S`의 간격을 가진 범위입니다. 각 요소 간의 단계는 일정하며, 범위는 타입 `T`의 `start`와 `stop`, 그리고 타입 `S`의 `step`으로 정의됩니다. `T`와 `S`는 모두 부동 소수점 타입이 아니어야 합니다. `a:b:c` 구문은 `b != 0`이고 `a`, `b`, `c`가 모두 정수일 때 `StepRange`를 생성합니다.

# 예제

```jldoctest
julia> collect(StepRange(1, Int8(2), 10))
5-element Vector{Int64}:
 1
 3
 5
 7
 9

julia> typeof(StepRange(1, Int8(2), 10))
StepRange{Int64, Int8}

julia> typeof(1:3:6)
StepRange{Int64, Int64}
```
