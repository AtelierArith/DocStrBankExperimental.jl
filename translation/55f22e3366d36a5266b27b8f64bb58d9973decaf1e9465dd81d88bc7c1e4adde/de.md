```
schur!(A) -> F::Schur
```

Dasselbe wie [`schur`](@ref), verwendet jedoch das Eingabeargument `A` als Arbeitsbereich.

# Beispiele

```jldoctest
julia> A = [5. 7.; -2. -4.]
2×2 Matrix{Float64}:
  5.0   7.0
 -2.0  -4.0

julia> F = schur!(A)
Schur{Float64, Matrix{Float64}, Vector{Float64}}
T-Faktor:
2×2 Matrix{Float64}:
 3.0   9.0
 0.0  -2.0
Z-Faktor:
2×2 Matrix{Float64}:
  0.961524  0.274721
 -0.274721  0.961524
Eigenwerte:
2-element Vector{Float64}:
  3.0
 -2.0

julia> A
2×2 Matrix{Float64}:
 3.0   9.0
 0.0  -2.0
```
