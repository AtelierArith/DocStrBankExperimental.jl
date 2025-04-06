```
spzeros([tip,]m[,n])
```

`m` uzunluğunda bir seyrek vektör veya `m x n` boyutunda bir seyrek matris oluşturur. Bu seyrek dizi, herhangi bir sıfır olmayan değer içermeyecektir. Yapım sırasında sıfır olmayan değerler için herhangi bir depolama alanı ayrılmayacaktır. Tip belirtilmezse varsayılan olarak [`Float64`](@ref) kullanılır.

# Örnekler

```jldoctest
julia> spzeros(3, 3)
3×3 SparseMatrixCSC{Float64, Int64} with 0 stored entries:
  ⋅    ⋅    ⋅
  ⋅    ⋅    ⋅
  ⋅    ⋅    ⋅

julia> spzeros(Float32, 4)
4-element SparseVector{Float32, Int64} with 0 stored entries
```
