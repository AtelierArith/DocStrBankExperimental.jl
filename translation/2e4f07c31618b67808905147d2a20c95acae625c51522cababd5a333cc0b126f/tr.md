```
sylvester(A, B, C)
```

Sylvester denklemi `AX + XB + C = 0` için çözüm `X`'i hesaplar; burada `A`, `B` ve `C` uyumlu boyutlara sahiptir ve `A` ile `-B`'nin eşit gerçek parçaya sahip özdeğerleri yoktur.

# Örnekler

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
