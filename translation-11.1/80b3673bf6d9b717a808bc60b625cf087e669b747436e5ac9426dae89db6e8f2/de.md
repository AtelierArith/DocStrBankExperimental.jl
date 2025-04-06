```
eigen(A; permute::Bool=true, scale::Bool=true, sortby) -> Eigen
```

Berechnen Sie die Eigenwertzerlegung von `A`, wobei ein [`Eigen`](@ref) Faktorisierungsobjekt `F` zurückgegeben wird, das die Eigenwerte in `F.values` und die Eigenvektoren in den Spalten der Matrix `F.vectors` enthält. Dies entspricht der Lösung eines Eigenwertproblems der Form `Ax =  λx`, wobei `A` eine Matrix ist, `x` ein Eigenvektor und `λ` ein Eigenwert. (Der `k`-te Eigenvektor kann aus dem Slice `F.vectors[:, k]` abgerufen werden.)

Das Iterieren über die Zerlegung produziert die Komponenten `F.values` und `F.vectors`.

Die folgenden Funktionen sind für `Eigen`-Objekte verfügbar: [`inv`](@ref), [`det`](@ref) und [`isposdef`](@ref).

Für allgemeine unsymmetrische Matrizen ist es möglich, anzugeben, wie die Matrix vor der Berechnung der Eigenvektoren balanciert werden soll. Die Option `permute=true` permutiert die Matrix, um näher an eine obere Dreiecksmatrix zu gelangen, und `scale=true` skaliert die Matrix durch ihre Diagonalelemente, um Zeilen und Spalten in der Norm gleichmäßiger zu machen. Der Standardwert ist `true` für beide Optionen.

Standardmäßig werden die Eigenwerte und -vektoren lexikografisch nach `(real(λ),imag(λ))` sortiert. Eine andere Vergleichsfunktion `by(λ)` kann an `sortby` übergeben werden, oder Sie können `sortby=nothing` übergeben, um die Eigenwerte in einer beliebigen Reihenfolge zu belassen. Einige spezielle Matrizenarten (z. B. [`Diagonal`](@ref) oder [`SymTridiagonal`](@ref)) können ihre eigene Sortierkonvention implementieren und akzeptieren möglicherweise kein `sortby`-Schlüsselwort.

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

julia> vals, vecs = F; # destrukturieren über Iteration

julia> vals == F.values && vecs == F.vectors
true
```
