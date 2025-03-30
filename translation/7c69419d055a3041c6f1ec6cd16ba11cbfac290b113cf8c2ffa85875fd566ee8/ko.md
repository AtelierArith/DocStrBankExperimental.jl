```
isposdef!(A) -> Bool
```

행렬이 양의 정부호(및 에르미트)인지 확인하기 위해 `A`의 Cholesky 분해를 시도하여 `A`를 덮어씁니다. [`isposdef`](@ref)도 참조하십시오.

# 예제

```jldoctest
julia> A = [1. 2.; 2. 50.];

julia> isposdef!(A)
true

julia> A
2×2 Matrix{Float64}:
 1.0  2.0
 2.0  6.78233
```
