```
isposdef(A) -> Bool
```

행렬이 양의 정부호(및 에르미트)인지 확인하기 위해 `A`의 콜레스키 분해를 시도합니다.

자세한 내용은 [`isposdef!`](@ref), [`cholesky`](@ref)를 참조하세요.

# 예제

```jldoctest
julia> A = [1 2; 2 50]
2×2 Matrix{Int64}:
 1   2
 2  50

julia> isposdef(A)
true
```
