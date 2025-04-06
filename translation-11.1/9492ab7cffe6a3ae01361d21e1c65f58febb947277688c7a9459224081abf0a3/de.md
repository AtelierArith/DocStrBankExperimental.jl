```
eigen(A, B; sortby) -> GeneralizedEigen
```

Berechnen Sie die verallgemeinerte Eigenwertzerlegung von `A` und `B`, wobei ein [`GeneralizedEigen`](@ref) Faktorisierungsobjekt `F` zurückgegeben wird, das die verallgemeinerten Eigenwerte in `F.values` und die verallgemeinerten Eigenvektoren in den Spalten der Matrix `F.vectors` enthält. Dies entspricht der Lösung eines verallgemeinerten Eigenwertproblems der Form `Ax =  λBx`, wobei `A, B` Matrizen sind, `x` ein Eigenvektor ist und `λ` ein Eigenwert ist. (Der `k`-te verallgemeinerte Eigenvektor kann aus dem Slice `F.vectors[:, k]` abgerufen werden.)

Das Iterieren über die Zerlegung erzeugt die Komponenten `F.values` und `F.vectors`.

Standardmäßig sind die Eigenwerte und -vektoren lexikografisch nach `(real(λ),imag(λ))` sortiert. Eine andere Vergleichsfunktion `by(λ)` kann an `sortby` übergeben werden, oder Sie können `sortby=nothing` übergeben, um die Eigenwerte in einer beliebigen Reihenfolge zu belassen.

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

julia> F = eigen(A, B);

julia> F.values
2-element Vector{ComplexF64}:
 0.0 - 1.0im
 0.0 + 1.0im

julia> F.vectors
2×2 Matrix{ComplexF64}:
  0.0+1.0im   0.0-1.0im
 -1.0+0.0im  -1.0-0.0im

julia> vals, vecs = F; # Destrukturierung durch Iteration

julia> vals == F.values && vecs == F.vectors
true
```
