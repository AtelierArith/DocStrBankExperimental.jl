```
schur(A) -> F::Schur
```

Berechnet die Schur-Faktorisierung der Matrix `A`. Der (quasi) dreieckige Schur-Faktor kann aus dem `Schur`-Objekt `F` entweder mit `F.Schur` oder `F.T` abgerufen werden, und die orthogonalen/einheitlichen Schur-Vektoren können mit `F.vectors` oder `F.Z` abgerufen werden, sodass `A = F.vectors * F.Schur * F.vectors'`. Die Eigenwerte von `A` können mit `F.values` abgerufen werden.

Für reelles `A` ist die Schur-Faktorisierung "quasitriangular", was bedeutet, dass sie oberdreieckig ist, außer mit 2×2-Diagonalblöcken für jedes konjugierte Paar komplexer Eigenwerte; dies ermöglicht es, die Faktorisierung rein reell zu halten, selbst wenn komplexe Eigenwerte vorhanden sind. Um die (komplexe) rein oberdreieckige Schur-Faktorisierung aus einer reellen quasitriangularen Faktorisierung zu erhalten, können Sie `Schur{Complex}(schur(A))` verwenden.

Die Iteration der Zerlegung produziert die Komponenten `F.T`, `F.Z` und `F.values`.

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

julia> t, z, vals = F; # Destrukturierung durch Iteration

julia> t == F.T && z == F.Z && vals == F.values
true
```
