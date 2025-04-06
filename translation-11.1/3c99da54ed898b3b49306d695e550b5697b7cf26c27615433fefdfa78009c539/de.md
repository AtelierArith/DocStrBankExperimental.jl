```
inv(M)
```

Matrixinversion. Berechnet die Matrix `N`, sodass `M * N = I`, wobei `I` die Einheitsmatrix ist. Berechnet durch Lösen der Linksdivision `N = M \ I`.

# Beispiele

```jldoctest
julia> M = [2 5; 1 3]
2×2 Matrix{Int64}:
 2  5
 1  3

julia> N = inv(M)
2×2 Matrix{Float64}:
  3.0  -5.0
 -1.0   2.0

julia> M*N == N*M == Matrix(I, 2, 2)
true
```
