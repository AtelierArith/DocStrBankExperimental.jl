```
Threads.Atomic{T}
```

타입 `T`의 객체에 대한 참조를 보유하며, 이는 원자적으로 접근되도록 보장합니다. 즉, 스레드 안전한 방식으로 접근됩니다.

원자적으로 사용할 수 있는 "단순한" 타입은 제한적이며, 기본적인 불리언, 정수 및 부동 소수점 타입입니다. 이들은 `Bool`, `Int8`...`Int128`, `UInt8`...`UInt128`, 및 `Float16`...`Float64`입니다.

새로운 원자 객체는 비원자 값에서 생성할 수 있으며, 지정하지 않으면 원자 객체는 0으로 초기화됩니다.

원자 객체는 `[]` 표기법을 사용하여 접근할 수 있습니다:

# 예제

```jldoctest
julia> x = Threads.Atomic{Int}(3)
Base.Threads.Atomic{Int64}(3)

julia> x[] = 1
1

julia> x[]
1
```

원자 작업은 [`atomic_`](@ref) 접두사를 사용하며, 예를 들어 [`atomic_add!`](@ref), [`atomic_xchg!`](@ref) 등이 있습니다.
