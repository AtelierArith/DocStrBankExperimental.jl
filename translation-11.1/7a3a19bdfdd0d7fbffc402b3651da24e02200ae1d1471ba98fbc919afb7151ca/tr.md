```
lyap(A, C)
```

Sürekli Lyapunov denklemi `AX + XA' + C = 0` için `X` çözümünü hesaplar; burada `A`'nın hiçbir özdeğeri sıfır reel parçaya sahip değildir ve iki özdeğeri birbirinin negatif karmaşık eşleniği değildir.

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

julia> X = lyap(A, B)
2×2 Matrix{Float64}:
  0.5  -0.5
 -0.5   0.25

julia> A*X + X*A' ≈ -B
true
```
