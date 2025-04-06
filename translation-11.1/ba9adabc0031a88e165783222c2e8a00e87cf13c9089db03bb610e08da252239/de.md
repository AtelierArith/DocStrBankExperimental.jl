```
Eigen <: Factorization
```

Matrixfaktorisierungstyp der Eigenwert-/Spektralzerlegung einer quadratischen Matrix `A`. Dies ist der Rückgabetyp von [`eigen`](@ref), der entsprechenden Matrixfaktorierungsfunktion.

Wenn `F::Eigen` das Faktorisierungsobjekt ist, können die Eigenwerte über `F.values` und die Eigenvektoren als Spalten der Matrix `F.vectors` abgerufen werden. (Der `k`-te Eigenvektor kann aus dem Slice `F.vectors[:, k]` abgerufen werden.)

Das Iterieren über die Zerlegung erzeugt die Komponenten `F.values` und `F.vectors`.

# Beispiele

```jldoctest
julia> F = eigen([1.0 0.0 0.0; 0.0 3.0 0.0; 0.0 0.0 18.0])
Eigen{Float64, Float64, Matrix{Float64}, Vector{Float64}}
values:
3-element Vector{Float64}:
  1.0
  3.0
 18.0
vectors:
3×3 Matrix{Float64}:
 1.0  0.0  0.0
 0.0  1.0  0.0
 0.0  0.0  1.0

julia> F.values
3-element Vector{Float64}:
  1.0
  3.0
 18.0

julia> F.vectors
3×3 Matrix{Float64}:
 1.0  0.0  0.0
 0.0  1.0  0.0
 0.0  0.0  1.0

julia> vals, vecs = F; # destructuring via iteration

julia> vals == F.values && vecs == F.vectors
true
```
