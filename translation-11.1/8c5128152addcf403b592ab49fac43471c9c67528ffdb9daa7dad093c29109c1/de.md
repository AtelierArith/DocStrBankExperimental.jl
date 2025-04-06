```
mapslices(f, A; dims)
```

Transformiere die angegebenen Dimensionen des Arrays `A`, indem eine Funktion `f` auf jede Scheibe der Form `A[..., :, ..., :, ...]` angewendet wird, mit einem Doppelpunkt an jeder `d` in `dims`. Die Ergebnisse werden entlang der verbleibenden Dimensionen zusammengefügt.

Zum Beispiel, wenn `dims = [1,2]` und `A` 4-dimensional ist, dann wird `f` auf `x = A[:,:,i,j]` für alle `i` und `j` aufgerufen, und `f(x)` wird zu `R[:,:,i,j]` im Ergebnis `R`.

Siehe auch [`eachcol`](@ref) oder [`eachslice`](@ref), verwendet mit [`map`](@ref) oder [`stack`](@ref).

# Beispiele

```jldoctest
julia> A = reshape(1:30,(2,5,3))
2×5×3 reshape(::UnitRange{Int64}, 2, 5, 3) mit eltype Int64:
[:, :, 1] =
 1  3  5  7   9
 2  4  6  8  10

[:, :, 2] =
 11  13  15  17  19
 12  14  16  18  20

[:, :, 3] =
 21  23  25  27  29
 22  24  26  28  30

julia> f(x::Matrix) = fill(x[1,1], 1,4);  # gibt eine 1×4 Matrix zurück

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

julia> g(x) = x[begin] // x[end-1];  # gibt eine Zahl zurück

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

Beachte, dass in `eachslice(A; dims=2)` die angegebene Dimension diejenige ist, *ohne* einen Doppelpunkt in der Scheibe. Dies ist `view(A,:,i,:)`, während `mapslices(f, A; dims=(1,3))` `A[:,i,:]` verwendet. Die Funktion `f` kann Werte in der Scheibe ändern, ohne `A` zu beeinflussen.
