```
something(x...)
```

인수 중 [`nothing`](@ref)과 같지 않은 첫 번째 값을 반환합니다. 그렇지 않으면 오류를 발생시킵니다. [`Some`](@ref) 유형의 인수는 언랩됩니다.

또한 [`coalesce`](@ref), [`skipmissing`](@ref), [`@something`](@ref)를 참조하십시오.

# 예제

```jldoctest
julia> something(nothing, 1)
1

julia> something(Some(1), nothing)
1

julia> something(Some(nothing), 2) === nothing
true

julia> something(missing, nothing)
missing

julia> something(nothing, nothing)
ERROR: ArgumentError: No value arguments present
```
