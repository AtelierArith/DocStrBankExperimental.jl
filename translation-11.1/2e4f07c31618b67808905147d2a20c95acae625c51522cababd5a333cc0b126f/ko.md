```
sylvester(A, B, C)
```

실베스터 방정식 `AX + XB + C = 0`의 해 `X`를 계산합니다. 여기서 `A`, `B` 및 `C`는 호환 가능한 차원을 가지며 `A`와 `-B`는 실수가 같은 고유값을 가지지 않습니다.

# 예제

```jldoctest
julia> A = [3. 4.; 5. 6]
2×2 Matrix{Float64}:
 3.0  4.0
 5.0  6.0

julia> B = [1. 1.; 1. 2.]
2×2 Matrix{Float64}:
 1.0  1.0
 1.0  2.0

julia> C = [1. 2.; -2. 1]
2×2 Matrix{Float64}:
  1.0  2.0
 -2.0  1.0

julia> X = sylvester(A, B, C)
2×2 Matrix{Float64}:
 -4.46667   1.93333
  3.73333  -1.8

julia> A*X + X*B ≈ -C
true
```
