```
coalesce(x...)
```

인수 중에서 [`missing`](@ref)과 같지 않은 첫 번째 값을 반환합니다. 만약 그런 값이 없다면 `missing`을 반환합니다.

또한 [`skipmissing`](@ref), [`something`](@ref), [`@coalesce`](@ref)도 참조하세요.

# 예제

```jldoctest
julia> coalesce(missing, 1)
1

julia> coalesce(1, missing)
1

julia> coalesce(nothing, 1)  # `nothing`을 반환합니다.

julia> coalesce(missing, missing)
missing
```
