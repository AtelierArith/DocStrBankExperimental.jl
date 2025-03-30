```
splice!(a::Vector, indices, [replacement]) -> items
```

Belirtilen indekslerdeki öğeleri kaldırır ve kaldırılan öğeleri içeren bir koleksiyonu döndürür. Sonraki öğeler, oluşan boşlukları doldurmak için sola kaydırılır. Belirtilmişse, sıralı bir koleksiyondan gelen yer tutucu değerler kaldırılan öğelerin yerine yerleştirilecektir; bu durumda, `indices` bir `AbstractUnitRange` olmalıdır.

Herhangi bir öğeyi kaldırmadan bir indeks `n` öncesine `replacement` eklemek için `splice!(collection, n:n-1, replacement)` kullanın.

!!! warning
    Herhangi bir değiştirilmiş argümanın, diğer bir argümanla bellek paylaşması durumunda davranış beklenmedik olabilir.


!!! compat "Julia 1.5"
    Julia 1.5'ten önce, `indices` her zaman bir `UnitRange` olmalıdır.


!!! compat "Julia 1.8"
    Julia 1.8'den önce, yer tutucu değerler ekleniyorsa `indices` bir `UnitRange` olmalıdır.


# Örnekler

```jldoctest
julia> A = [-1, -2, -3, 5, 4, 3, -1]; splice!(A, 4:3, 2)
Int64[]

julia> A
8-element Vector{Int64}:
 -1
 -2
 -3
  2
  5
  4
  3
 -1
```
