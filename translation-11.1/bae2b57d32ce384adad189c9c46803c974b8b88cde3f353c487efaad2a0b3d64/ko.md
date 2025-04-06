```
eigvecs(A, B) -> Matrix
```

행렬 `M`을 반환하며, `M`의 열은 `A`와 `B`의 일반화된 고유벡터입니다. (`k`번째 고유벡터는 슬라이스 `M[:, k]`에서 얻을 수 있습니다.)

# 예제

```jldoctest
julia> A = [1 0; 0 -1]
2×2 Matrix{Int64}:
 1   0
 0  -1

julia> B = [0 1; 1 0]
2×2 Matrix{Int64}:
 0  1
 1  0

julia> eigvecs(A, B)
2×2 Matrix{ComplexF64}:
  0.0+1.0im   0.0-1.0im
 -1.0+0.0im  -1.0-0.0im
```
