```
promote_type(type1, type2, ...)
```

프로모션은 혼합된 타입의 값을 단일 공통 타입으로 변환하는 것을 의미합니다. `promote_type`은 서로 다른 타입의 인수를 받을 때 Julia에서 기본 프로모션 동작을 나타냅니다. `promote_type`은 일반적으로 과도하게 넓히지 않으면서 두 입력 타입 중 대부분의 값을 근사할 수 있는 타입을 반환하려고 합니다. 일부 손실은 허용됩니다. 예를 들어, `promote_type(Int64, Float64)`는 [`Float64`](@ref)를 반환하지만, 엄밀히 말하면 모든 [`Int64`](@ref) 값이 정확하게 `Float64` 값으로 표현될 수는 없습니다.

참고: [`promote`](@ref), [`promote_typejoin`](@ref), [`promote_rule`](@ref).

# 예제

```jldoctest
julia> promote_type(Int64, Float64)
Float64

julia> promote_type(Int32, Int64)
Int64

julia> promote_type(Float32, BigInt)
BigFloat

julia> promote_type(Int16, Float16)
Float16

julia> promote_type(Int64, Float16)
Float16

julia> promote_type(Int8, UInt16)
UInt16
```

!!! 경고 "이것을 직접 오버로드하지 마세요"     자신의 타입에 대한 프로모션을 오버로드하려면 [`promote_rule`](@ref)를 오버로드해야 합니다. `promote_type`은 내부적으로 타입을 결정하기 위해 `promote_rule`을 호출합니다. `promote_type`을 직접 오버로드하면 모호성 오류가 발생할 수 있습니다.
