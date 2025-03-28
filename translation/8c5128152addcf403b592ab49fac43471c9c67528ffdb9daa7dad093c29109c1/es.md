```
mapslices(f, A; dims)
```

Transforma las dimensiones dadas del arreglo `A` aplicando una función `f` en cada rebanada de la forma `A[..., :, ..., :, ...]`, con dos puntos en cada `d` en `dims`. Los resultados se concatenan a lo largo de las dimensiones restantes.

Por ejemplo, si `dims = [1,2]` y `A` es de 4 dimensiones, entonces `f` se llama sobre `x = A[:,:,i,j]` para todos los `i` y `j`, y `f(x)` se convierte en `R[:,:,i,j]` en el resultado `R`.

Véase también [`eachcol`](@ref) o [`eachslice`](@ref), utilizados con [`map`](@ref) o [`stack`](@ref).

# Ejemplos

```jldoctest
julia> A = reshape(1:30,(2,5,3))
2×5×3 reshape(::UnitRange{Int64}, 2, 5, 3) con el tipo de elemento Int64:
[:, :, 1] =
 1  3  5  7   9
 2  4  6  8  10

[:, :, 2] =
 11  13  15  17  19
 12  14  16  18  20

[:, :, 3] =
 21  23  25  27  29
 22  24  26  28  30

julia> f(x::Matrix) = fill(x[1,1], 1,4);  # devuelve una matriz 1×4

julia> B = mapslices(f, A, dims=(1,2))
1×4×3 Array{Int64, 3}:
[:, :, 1] =
 1  1  1  1

[:, :, 2] =
 11  11  11  11

[:, :, 3] =
 21  21  21  21

julia> f2(x::AbstractMatrix) = fill(x[1,1], 1,4);

julia> B == stack(f2, eachslice(A, dims=3))
true

julia> g(x) = x[begin] // x[end-1];  # devuelve un número

julia> mapslices(g, A, dims=[1,3])
1×5×1 Array{Rational{Int64}, 3}:
[:, :, 1] =
 1//21  3//23  1//5  7//27  9//29

julia> map(g, eachslice(A, dims=2))
Vector de 5 elementos {Rational{Int64}}:
 1//21
 3//23
 1//5
 7//27
 9//29

julia> mapslices(sum, A; dims=(1,3)) == sum(A; dims=(1,3))
true
```

Observe que en `eachslice(A; dims=2)`, la dimensión especificada es la que *no* tiene un dos puntos en la rebanada. Esto es `view(A,:,i,:)`, mientras que `mapslices(f, A; dims=(1,3))` utiliza `A[:,i,:]`. La función `f` puede mutar valores en la rebanada sin afectar a `A`.
