```
^(A::AbstractMatrix, p::Number)
```

행렬 거듭제곱, $\exp(p\log(A))$와 동등함

# 예제

```jldoctest
julia> [1 2; 0 3]^3
2×2 Matrix{Int64}:
 1  26
 0  27
```
