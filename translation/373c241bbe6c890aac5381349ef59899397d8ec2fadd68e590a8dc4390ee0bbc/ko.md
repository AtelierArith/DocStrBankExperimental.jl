```
Matrix{T}(nothing, m, n)
```

`m`×`n` 크기의 [`Matrix{T}`](@ref)를 생성하며, [`nothing`](@ref) 항목으로 초기화됩니다. 요소 유형 `T`는 이러한 값을 저장할 수 있어야 하며, 즉 `Nothing <: T` 여야 합니다.

# 예제

```jldoctest
julia> Matrix{Union{Nothing, String}}(nothing, 2, 3)
2×3 Matrix{Union{Nothing, String}}:
 nothing  nothing  nothing
 nothing  nothing  nothing
```
