```
GeneralizedEigen <: Factorization
```

Matrixfaktorisierungstyp der verallgemeinerten Eigenwert-/Spektralzerlegung von `A` und `B`. Dies ist der Rückgabetyp von [`eigen`](@ref), der entsprechenden Matrixfaktorierungsfunktion, wenn sie mit zwei Matrixargumenten aufgerufen wird.

Wenn `F::GeneralizedEigen` das Faktorisierungsobjekt ist, können die Eigenwerte über `F.values` und die Eigenvektoren als Spalten der Matrix `F.vectors` abgerufen werden. (Der `k`-te Eigenvektor kann aus dem Slice `F.vectors[:, k]` abgerufen werden.)

Das Iterieren über die Zerlegung erzeugt die Komponenten `F.values` und `F.vectors`.

# Beispiele

```jldoctest
julia> A = [1 0; 0 -1]
2×2 Matrix{Int64}:
 1   0
 0  -1

julia> B = [0 1; 1 0]
2×2 Matrix{Int64}:
 0  1
 1  0

julia> F = eigen(A, B)
GeneralizedEigen{ComplexF64, ComplexF64, Matrix{ComplexF64}, Vector{ComplexF64}}
values:
2-element Vector{ComplexF64}:
 0.0 - 1.0im
 0.0 + 1.0im
vectors:
2×2 Matrix{ComplexF64}:
  0.0+1.0im   0.0-1.0im
 -1.0+0.0im  -1.0-0.0im

julia> F.values
2-element Vector{ComplexF64}:
 0.0 - 1.0im
 0.0 + 1.0im

julia> F.vectors
2×2 Matrix{ComplexF64}:
  0.0+1.0im   0.0-1.0im
 -1.0+0.0im  -1.0-0.0im

julia> vals, vecs = F; # destructuring via iteration

julia> vals == F.values && vecs == F.vectors
true
```
