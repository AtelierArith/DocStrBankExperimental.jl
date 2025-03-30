```
promote_typejoin(T, S)
```

`T`와 `S`를 모두 포함하는 타입을 계산합니다. 이는 두 타입의 부모일 수도 있고, 적절한 경우 `Union`일 수도 있습니다. [`typejoin`](@ref)으로 대체됩니다.

대신 [`promote`](@ref), [`promote_type`](@ref)를 참조하세요.

# 예제

```jldoctest
julia> Base.promote_typejoin(Int, Float64)
Real

julia> Base.promote_type(Int, Float64)
Float64
```
