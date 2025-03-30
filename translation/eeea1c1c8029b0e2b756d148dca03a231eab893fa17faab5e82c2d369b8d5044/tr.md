```
SparseVector{Tv,Ti<:Integer} <: AbstractSparseVector{Tv,Ti}
```

Seyrek vektörleri depolamak için vektör türü. Vektörün uzunluğunu, sıralı bir sıfırdan farklı indeksler vektörünü ve sıfırdan farklı değerler vektörünü geçirerek oluşturulabilir.

Örneğin, `[5, 6, 0, 7]` vektörü şu şekilde temsil edilebilir:

```julia
SparseVector(4, [1, 2, 4], [5, 6, 7])
```

Bu, indeks 1'de 5, indeks 2'de 6, indeks 3'te `zero(Int)` ve indeks 4'te 7 olduğunu gösterir.

Seyrek vektörleri, `sparse` kullanarak yoğun vektörlerden doğrudan oluşturmak daha pratik olabilir:

```julia
sparse([5, 6, 0, 7])
```

aynı seyrek vektörü verir.
