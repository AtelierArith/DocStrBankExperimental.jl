```
lyap(A, C)
```

연속 리아푸노프 방정식 `AX + XA' + C = 0`의 해 `X`를 계산합니다. 여기서 `A`의 고유값 중 어떤 것도 실수가 0인 부분을 가지지 않으며, 두 개의 고유값이 서로 음의 복소수 켤레가 아닙니다.

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

julia> X = lyap(A, B)
2×2 Matrix{Float64}:
  0.5  -0.5
 -0.5   0.25

julia> A*X + X*A' ≈ -B
true
```
