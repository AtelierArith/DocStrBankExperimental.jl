```
Vector{T}(missing, m)
```

길이가 `m`인 [`Vector{T}`](@ref)를 생성하며, [`missing`](@ref) 항목으로 초기화됩니다. 요소 유형 `T`는 이러한 값을 수용할 수 있어야 하며, 즉 `Missing <: T`여야 합니다.

# 예제

```jldoctest
julia> Vector{Union{Missing, String}}(missing, 2)
2-element Vector{Union{Missing, String}}:
 missing
 missing
```
