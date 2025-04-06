```
lmul!(A, B)
```

Calcula el producto de matrices $AB$, sobrescribiendo `B`, y devuelve el resultado. Aquí, `A` debe ser de un tipo de matriz especial, como, por ejemplo, [`Diagonal`](@ref), [`UpperTriangular`](@ref) o [`LowerTriangular`](@ref), o de algún tipo ortogonal, ver [`QR`](@ref).

# Ejemplos

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
