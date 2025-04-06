```
rmul!(A, B)
```

Berechne das Matrix-Matrix-Produkt $AB$, überschreibe `A` und gib das Ergebnis zurück. Hier muss `B` von einem speziellen Matrizen-Typ sein, wie z.B. [`Diagonal`](@ref), [`UpperTriangular`](@ref) oder [`LowerTriangular`](@ref), oder von einem orthogonalen Typ, siehe [`QR`](@ref).

# Beispiele

```jldoctest
julia> A = [0 1; 1 0];

julia> B = UpperTriangular([1 2; 0 3]);

julia> rmul!(A, B);

julia> A
2×2 Matrix{Int64}:
 0  3
 1  2

julia> A = [1.0 2.0; 3.0 4.0];

julia> F = qr([0 1; -1 0]);

julia> rmul!(A, F.Q)
2×2 Matrix{Float64}:
 2.0  1.0
 4.0  3.0
```
