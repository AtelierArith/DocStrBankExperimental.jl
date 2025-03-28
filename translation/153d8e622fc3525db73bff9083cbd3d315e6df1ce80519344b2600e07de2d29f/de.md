```
Bidiagonal(A, uplo::Symbol)
```

Konstruiere eine `Bidiagonal`-Matrix aus der Hauptdiagonale von `A` und ihrer ersten Über- (wenn `uplo=:U`) oder Unterdiagonale (wenn `uplo=:L`).

# Beispiele

```jldoctest
julia> A = [1 1 1 1; 2 2 2 2; 3 3 3 3; 4 4 4 4]
4×4 Matrix{Int64}:
 1  1  1  1
 2  2  2  2
 3  3  3  3
 4  4  4  4

julia> Bidiagonal(A, :U) # enthält die Hauptdiagonale und die erste Überdiagonale von A
4×4 Bidiagonal{Int64, Vector{Int64}}:
 1  1  ⋅  ⋅
 ⋅  2  2  ⋅
 ⋅  ⋅  3  3
 ⋅  ⋅  ⋅  4

julia> Bidiagonal(A, :L) # enthält die Hauptdiagonale und die erste Unterdiagonale von A
4×4 Bidiagonal{Int64, Vector{Int64}}:
 1  ⋅  ⋅  ⋅
 2  2  ⋅  ⋅
 ⋅  3  3  ⋅
 ⋅  ⋅  4  4
```
