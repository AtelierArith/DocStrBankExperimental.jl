```
Matrix{T}(undef, m, n)
```

초기화되지 않은 [`Matrix{T}`](@ref) 크기 `m`×`n`의 행렬을 생성합니다.

# 예제

```julia-repl
julia> Matrix{Float64}(undef, 2, 3)
2×3 Array{Float64, 2}:
 2.36365e-314  2.28473e-314    5.0e-324
 2.26704e-314  2.26711e-314  NaN

julia> similar(ans, Int32, 2, 2)
2×2 Matrix{Int32}:
 490537216  1277177453
         1  1936748399
```
