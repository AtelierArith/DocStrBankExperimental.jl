```
append!(collection, collections...) -> collection.
```

Sıralı bir konteyner `collection` için, her `collections`'ın elemanlarını sonuna ekleyin.

!!! compat "Julia 1.6"
    Birden fazla koleksiyonun eklenmesi, en az Julia 1.6 gerektirir.


# Örnekler

```jldoctest
julia> append!([1], [2, 3])
3-element Vector{Int64}:
 1
 2
 3

julia> append!([1, 2, 3], [4, 5], [6])
6-element Vector{Int64}:
 1
 2
 3
 4
 5
 6
```

`collection`'a, başka bir koleksiyonda zaten bulunmayan bireysel öğeleri eklemek için [`push!`](@ref) kullanın. Önceki örneğin sonucu, `push!([1, 2, 3], 4, 5, 6)` ile eşdeğerdir.

Performans modeli hakkında notlar için [`sizehint!`](@ref) bakın.

Ayrıca, vektörler için [`vcat`](@ref), kümeler için [`union!`](@ref) ve ters sıradaki işlemler için [`prepend!`](@ref) ve [`pushfirst!`](@ref) ile ilgili daha fazla bilgiye bakın.
