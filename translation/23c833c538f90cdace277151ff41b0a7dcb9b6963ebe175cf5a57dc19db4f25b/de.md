```
lmul!(A, B)
```

Berechnen Sie das Matrix-Matrix-Produkt $AB$, überschreiben Sie `B` und geben Sie das Ergebnis zurück. Hier muss `A` von einem speziellen Matrizen-Typ sein, wie z.B. [`Diagonal`](@ref), [`UpperTriangular`](@ref) oder [`LowerTriangular`](@ref), oder von einem orthogonalen Typ, siehe [`QR`](@ref).

# Beispiele

```jldoctest
julia> B = [0 1; 1 0];

julia> A = UpperTriangular([1 2; 0 3]);

julia> lmul!(A, B);

julia> B
2×2 Matrix{Int64}:
 2  1
 3  0

julia> B = [1.0 2.0; 3.0 4.0];

julia> F = qr([0 1; -1 0]);

julia> lmul!(F.Q, B)
2×2 Matrix{Float64}:
 3.0  4.0
 1.0  2.0
```
