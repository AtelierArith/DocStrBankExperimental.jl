```
svd(A; full::Bool = false, alg::Algorithm = default_svd_alg(A)) -> SVD
```

Berechnet die singuläre Wertzerlegung (SVD) von `A` und gibt ein `SVD`-Objekt zurück.

`U`, `S`, `V` und `Vt` können aus der Faktorisierung `F` mit `F.U`, `F.S`, `F.V` und `F.Vt` abgerufen werden, sodass `A = U * Diagonal(S) * Vt`. Der Algorithmus erzeugt `Vt`, und daher ist es effizienter, `Vt` zu extrahieren als `V`. Die singulären Werte in `S` sind in absteigender Reihenfolge sortiert.

Das Iterieren über die Zerlegung erzeugt die Komponenten `U`, `S` und `V`.

Wenn `full = false` (Standard), wird eine "dünne" SVD zurückgegeben. Für eine $M \times N$-Matrix `A` ist in der vollen Faktorisierung `U` $M \times M$ und `V` $N \times N$, während in der dünnen Faktorisierung `U` $M \times K$ und `V` $N \times K$ ist, wobei $K = \min(M,N)$ die Anzahl der singulären Werte ist.

Wenn `alg = DivideAndConquer()` ein Divide-and-Conquer-Algorithmus verwendet wird, um die SVD zu berechnen. Eine andere (typischerweise langsamere, aber genauere) Option ist `alg = QRIteration()`.

!!! compat "Julia 1.3"
    Das Schlüsselwortargument `alg` erfordert Julia 1.3 oder später.


# Beispiele

```jldoctest
julia> A = rand(4,3);

julia> F = svd(A); # Speichern Sie das Faktorisierungsobjekt

julia> A ≈ F.U * Diagonal(F.S) * F.Vt
true

julia> U, S, V = F; # Destrukturierung über Iteration

julia> A ≈ U * Diagonal(S) * V'
true

julia> Uonly, = svd(A); # Speichern Sie nur U

julia> Uonly == U
true
```
