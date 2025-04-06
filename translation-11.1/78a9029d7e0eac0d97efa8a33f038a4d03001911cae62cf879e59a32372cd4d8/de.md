```
factorize(A)
```

Berechnet eine geeignete Faktorisierung von `A`, basierend auf dem Typ der Eingabematrix. `factorize` überprüft `A`, um festzustellen, ob es symmetrisch/triangular/etc. ist, wenn `A` als generische Matrix übergeben wird. `factorize` überprüft jedes Element von `A`, um jede Eigenschaft zu verifizieren/auszuschließen. Es wird sofort abgebrochen, sobald es Symmetrie/triangular Struktur ausschließen kann. Der Rückgabewert kann für eine effiziente Lösung mehrerer Systeme wiederverwendet werden. Zum Beispiel: `A=factorize(A); x=A\b; y=A\C`.

| Eigenschaften von `A`           | Art der Faktorisierung                       |
|:------------------------------- |:-------------------------------------------- |
| Positiv definit                 | Cholesky (siehe [`cholesky`](@ref))          |
| Dicht symmetrisch/Hermitesch    | Bunch-Kaufman (siehe [`bunchkaufman`](@ref)) |
| Spärlich symmetrisch/Hermitesch | LDLt (siehe [`ldlt`](@ref))                  |
| Triangular                      | Triangular                                   |
| Diagonal                        | Diagonal                                     |
| Bidiagonal                      | Bidiagonal                                   |
| Tridiagonal                     | LU (siehe [`lu`](@ref))                      |
| Symmetrisch reell tridiagonal   | LDLt (siehe [`ldlt`](@ref))                  |
| Allgemein quadratisch           | LU (siehe [`lu`](@ref))                      |
| Allgemein nicht-quadratisch     | QR (siehe [`qr`](@ref))                      |

Wenn `factorize` auf einer hermitischen positiv definiten Matrix aufgerufen wird, wird `factorize` beispielsweise eine Cholesky-Faktorisierung zurückgeben.

# Beispiele

```jldoctest
julia> A = Array(Bidiagonal(fill(1.0, (5, 5)), :U))
5×5 Matrix{Float64}:
 1.0  1.0  0.0  0.0  0.0
 0.0  1.0  1.0  0.0  0.0
 0.0  0.0  1.0  1.0  0.0
 0.0  0.0  0.0  1.0  1.0
 0.0  0.0  0.0  0.0  1.0

julia> factorize(A) # factorize wird überprüfen, ob A bereits faktorisierte ist
5×5 Bidiagonal{Float64, Vector{Float64}}:
 1.0  1.0   ⋅    ⋅    ⋅
  ⋅   1.0  1.0   ⋅    ⋅
  ⋅    ⋅   1.0  1.0   ⋅
  ⋅    ⋅    ⋅   1.0  1.0
  ⋅    ⋅    ⋅    ⋅   1.0
```

Dies gibt ein `5×5 Bidiagonal{Float64}` zurück, das nun an andere lineare Algebra-Funktionen (z. B. Eigenlöser) übergeben werden kann, die spezialisierte Methoden für `Bidiagonal`-Typen verwenden.
