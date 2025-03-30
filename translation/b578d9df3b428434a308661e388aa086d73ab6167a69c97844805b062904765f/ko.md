```
promote(xs...)
```

모든 인수를 공통 유형으로 변환하고, 모두 (튜플로) 반환합니다. 변환할 수 있는 인수가 없으면 오류가 발생합니다.

참고: [`promote_type`](@ref), [`promote_rule`](@ref).

# 예제

```jldoctest
julia> promote(Int8(1), Float16(4.5), Float32(4.1))
(1.0f0, 4.5f0, 4.1f0)

julia> promote_type(Int8, Float16, Float32)
Float32

julia> reduce(Base.promote_typejoin, (Int8, Float16, Float32))
Real

julia> promote(1, "x")
ERROR: promotion of types Int64 and String failed to change any arguments
[...]

julia> promote_type(Int, String)
Any
```
