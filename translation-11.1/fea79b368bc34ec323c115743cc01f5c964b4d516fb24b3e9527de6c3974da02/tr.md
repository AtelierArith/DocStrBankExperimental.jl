```
push!(collection, items...) -> collection
```

Bir veya daha fazla `items`'ı `collection`'a ekleyin. Eğer `collection` sıralı bir konteyner ise, öğeler sona (verilen sırada) eklenir.

# Örnekler

```jldoctest
julia> push!([1, 2, 3], 4, 5, 6)
6-element Vector{Int64}:
 1
 2
 3
 4
 5
 6
```

Eğer `collection` sıralı ise, başka bir koleksiyonun tüm elemanlarını eklemek için [`append!`](@ref) kullanın. Önceki örneğin sonucu, `append!([1, 2, 3], [4, 5, 6])` ile eşdeğerdir. `AbstractSet` nesneleri için, bunun yerine [`union!`](@ref) kullanılabilir.

Performans modeli hakkında notlar için [`sizehint!`](@ref) bakın.

Ayrıca [`pushfirst!`](@ref) ile ilgili de bilgi edinin.
