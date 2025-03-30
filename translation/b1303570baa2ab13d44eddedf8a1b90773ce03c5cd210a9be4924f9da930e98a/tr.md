```
unique!(A::AbstractVector)
```

[`isequal`](@ref) ve [`hash`](@ref) tarafından belirlenen tekrar eden öğeleri kaldırın, ardından değiştirilmiş `A`'yı döndürün. `unique!`, `A`'nın öğelerini meydana geldikleri sırayla döndürecektir. Eğer döndürülen verinin sırası ile ilgilenmiyorsanız, `(sort!(A); unique!(A))` çağrısı, `A`'nın öğeleri sıralanabiliyorsa çok daha verimli olacaktır.

# Örnekler

```jldoctest
julia> unique!([1, 1, 1])
1-element Vector{Int64}:
 1

julia> A = [7, 3, 2, 3, 7, 5];

julia> unique!(A)
4-element Vector{Int64}:
 7
 3
 2
 5

julia> B = [7, 6, 42, 6, 7, 42];

julia> sort!(B);  # unique! sıralı verileri çok daha verimli bir şekilde işleyebilir.

julia> unique!(B)
3-element Vector{Int64}:
  6
  7
 42
```
