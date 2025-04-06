```
rmul!(A, B)
```

Calcula el producto de matrices $AB$, sobrescribiendo `A`, y devuelve el resultado. Aquí, `B` debe ser de un tipo de matriz especial, como, por ejemplo, [`Diagonal`](@ref), [`UpperTriangular`](@ref) o [`LowerTriangular`](@ref), o de algún tipo ortogonal, ver [`QR`](@ref).

# Ejemplos

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
