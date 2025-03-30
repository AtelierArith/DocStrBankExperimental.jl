```
nonzeros(A)
```

Seyrek dizi `A` içindeki yapısal sıfır olmayan değerlerin bir vektörünü döndürür. Bu, seyrek dizide açıkça saklanan sıfırları da içerir. Döndürülen vektör, `A`'nın içsel sıfır olmayan depolamasına doğrudan işaret eder ve döndürülen vektördeki herhangi bir değişiklik, `A`'yı da değiştirecektir. [`rowvals`](@ref) ve [`nzrange`](@ref) bakınız.

# Örnekler

```jldoctest
julia> A = sparse(2I, 3, 3)
3×3 SparseMatrixCSC{Int64, Int64} with 3 stored entries:
 2  ⋅  ⋅
 ⋅  2  ⋅
 ⋅  ⋅  2

julia> nonzeros(A)
3-element Vector{Int64}:
 2
 2
 2
```
