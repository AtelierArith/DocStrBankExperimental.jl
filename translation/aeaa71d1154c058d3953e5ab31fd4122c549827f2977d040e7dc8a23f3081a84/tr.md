```
rmul!(A, B)
```

Matris-matris çarpımını $AB$ hesaplayın, `A`'yı üzerine yazarak sonucu döndürün. Burada, `B` özel matris türünde olmalıdır, örneğin, [`Diagonal`](@ref), [`UpperTriangular`](@ref) veya [`LowerTriangular`](@ref) gibi, ya da bazı ortogonal türlerde, bkz. [`QR`](@ref).

# Örnekler

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
