```
logdet(M)
```

Matris determinantının logaritması. `log(det(M))` ile eşdeğerdir, ancak daha fazla doğruluk sağlayabilir ve taşma/azalma sorunlarını önleyebilir.

# Örnekler

```jldoctest
julia> M = [1 0; 2 2]
2×2 Matrix{Int64}:
 1  0
 2  2

julia> logdet(M)
0.6931471805599453

julia> logdet(Matrix(I, 3, 3))
0.0
```
