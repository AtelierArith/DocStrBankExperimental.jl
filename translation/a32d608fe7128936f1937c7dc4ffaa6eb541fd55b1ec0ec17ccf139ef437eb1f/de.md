```
Schur <: Faktorisierung
```

Matrixfaktorisierungstyp der Schur-Faktorisierung einer Matrix `A`. Dies ist der Rückgabetyp von [`schur(_)`](@ref), der entsprechenden Matrixfaktorisierungsfunktion.

Wenn `F::Schur` das Faktorisierungsobjekt ist, kann der (quasi) dreieckige Schur-Faktor entweder über `F.Schur` oder `F.T` und die orthogonalen/einheitlichen Schur-Vektoren über `F.vectors` oder `F.Z` erhalten werden, sodass `A = F.vectors * F.Schur * F.vectors'`. Die Eigenwerte von `A` können mit `F.values` erhalten werden.

Das Iterieren über die Zerlegung produziert die Komponenten `F.T`, `F.Z` und `F.values`.

# Beispiele

```jldoctest
julia> A = [5. 7.; -2. -4.]
2×2 Matrix{Float64}:
  5.0   7.0
 -2.0  -4.0

julia> F = schur(A)
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

julia> F.vectors * F.Schur * F.vectors'
2×2 Matrix{Float64}:
  5.0   7.0
 -2.0  -4.0

julia> t, z, vals = F; # Destrukturierung über Iteration

julia> t == F.T && z == F.Z && vals == F.values
true
```
