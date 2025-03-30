```
get(val::ScopedValue{T})::Union{Nothing, Some{T}}
```

스코프 값이 설정되지 않았고 기본값이 없으면 `nothing`을 반환합니다. 그렇지 않으면 현재 값으로 `Some{T}`를 반환합니다.

참고: [`ScopedValues.with`](@ref), [`ScopedValues.@with`](@ref), [`ScopedValues.ScopedValue`](@ref).

# 예제

```jldoctest
julia> using Base.ScopedValues

julia> a = ScopedValue(42); b = ScopedValue{Int}();

julia> ScopedValues.get(a)
Some(42)

julia> isnothing(ScopedValues.get(b))
true
```
