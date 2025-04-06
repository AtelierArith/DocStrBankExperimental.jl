```
rmul!(A, B)
```

Calcule le produit matrice-matrice $AB$, en écrasant `A`, et retourne le résultat. Ici, `B` doit être d'un type de matrice spécial, comme, par exemple, [`Diagonal`](@ref), [`UpperTriangular`](@ref) ou [`LowerTriangular`](@ref), ou d'un type orthogonal, voir [`QR`](@ref).

# Exemples

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
