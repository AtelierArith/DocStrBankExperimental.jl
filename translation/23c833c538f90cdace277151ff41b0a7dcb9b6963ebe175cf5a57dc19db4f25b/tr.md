```
lmul!(A, B)
```

Matris-matris çarpımını $AB$ hesaplayın, `B`'yi üzerine yazarak sonucu döndürün. Burada, `A` özel matris türünde olmalıdır, örneğin, [`Diagonal`](@ref), [`UpperTriangular`](@ref) veya [`LowerTriangular`](@ref) gibi, ya da bazı ortogonal türlerde, bkz. [`QR`](@ref).

# Örnekler

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
