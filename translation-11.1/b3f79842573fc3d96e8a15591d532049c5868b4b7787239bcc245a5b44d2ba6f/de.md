```
svd!(A; full::Bool = false, alg::Algorithm = default_svd_alg(A)) -> SVD
```

`svd!` ist dasselbe wie [`svd`](@ref), speichert jedoch Platz, indem es die Eingabe `A` überschreibt, anstatt eine Kopie zu erstellen. Siehe Dokumentation von [`svd`](@ref) für Details.
