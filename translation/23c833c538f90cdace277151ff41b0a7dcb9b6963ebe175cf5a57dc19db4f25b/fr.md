```
lmul!(A, B)
```

Calcule le produit matriciel $AB$, en écrasant `B`, et retourne le résultat. Ici, `A` doit être d'un type de matrice spécial, comme, par exemple, [`Diagonal`](@ref), [`UpperTriangular`](@ref) ou [`LowerTriangular`](@ref), ou d'un type orthogonal, voir [`QR`](@ref).

# Exemples

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
