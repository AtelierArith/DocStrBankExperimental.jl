```
Matrix{T}(missing, m, n)
```

[`Matrix{T}`](@ref)의 크기 `m`×`n`을 생성하며, [`missing`](@ref) 항목으로 초기화됩니다. 요소 유형 `T`는 이러한 값을 저장할 수 있어야 하며, 즉 `Missing <: T`이어야 합니다.

# 예제

```jldoctest
julia> Matrix{Union{Missing, String}}(missing, 2, 3)
2×3 Matrix{Union{Missing, String}}:
 missing  missing  missing
 missing  missing  missing
```
