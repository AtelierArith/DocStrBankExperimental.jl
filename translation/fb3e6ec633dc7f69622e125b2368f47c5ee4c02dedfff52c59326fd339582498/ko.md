```
Vector{T}(nothing, m)
```

길이가 `m`인 [`Vector{T}`](@ref)를 생성하며, [`nothing`](@ref) 항목으로 초기화됩니다. 요소 유형 `T`는 이러한 값을 저장할 수 있어야 하며, 즉 `Nothing <: T`여야 합니다.

# 예제

```jldoctest
julia> Vector{Union{Nothing, String}}(nothing, 2)
2-element Vector{Union{Nothing, String}}:
 nothing
 nothing
```
