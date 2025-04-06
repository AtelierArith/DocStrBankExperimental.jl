```
mapslices(f, A; dims)
```

Verilen `A` dizisinin boyutlarını, her bir dilim için `A[..., :, ..., :, ...]` biçiminde bir fonksiyon `f` uygulayarak dönüştürür. Sonuçlar, kalan boyutlar boyunca birleştirilir.

Örneğin, eğer `dims = [1,2]` ve `A` 4 boyutlu ise, `f`, tüm `i` ve `j` için `x = A[:,:,i,j]` üzerinde çağrılır ve `f(x)` sonucu `R[:,:,i,j]` olur.

Ayrıca [`eachcol`](@ref) veya [`eachslice`](@ref) ile birlikte kullanılan [`map`](@ref) veya [`stack`](@ref) ile de bakabilirsiniz.

# Örnekler

```jldoctest
julia> A = reshape(1:30,(2,5,3))
2×5×3 reshape(::UnitRange{Int64}, 2, 5, 3) with eltype Int64:
[:, :, 1] =
 1  3  5  7   9
 2  4  6  8  10

[:, :, 2] =
 11  13  15  17  19
 12  14  16  18  20

[:, :, 3] =
 21  23  25  27  29
 22  24  26  28  30

julia> f(x::Matrix) = fill(x[1,1], 1,4);  # 1×4 matris döner

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

julia> g(x) = x[begin] // x[end-1];  # bir sayı döner

julia> mapslices(g, A, dims=[1,3])
1×5×1 Array{Rational{Int64}, 3}:
[:, :, 1] =
 1//21  3//23  1//5  7//27  9//29

julia> map(g, eachslice(A, dims=2))
5-element Vector{Rational{Int64}}:
 1//21
 3//23
 1//5
 7//27
 9//29

julia> mapslices(sum, A; dims=(1,3)) == sum(A; dims=(1,3))
true
```

`eachslice(A; dims=2)` ifadesinde, belirtilen boyut, dilimde *noktasız* olan boyuttur. Bu, `view(A,:,i,:)` iken, `mapslices(f, A; dims=(1,3))` `A[:,i,:]` kullanır. Fonksiyon `f`, dilimdeki değerleri değiştirerek `A`'yı etkilemeden çalışabilir.
