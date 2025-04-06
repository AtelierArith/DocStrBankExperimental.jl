```
peel([T,] ref::GitReference)
```

`ref`'i `T` türünde bir nesne elde edilene kadar özyinelemeli olarak soyulacaktır. Eğer `T` sağlanmazsa, `ref` bir [`GitTag`](@ref) dışındaki bir nesne elde edilene kadar soyulacaktır.

  * Bir `GitTag`, referans verdiği nesneye soyulacaktır.
  * Bir [`GitCommit`](@ref), bir [`GitTree`](@ref) nesnesine soyulacaktır.

!!! not
    Sadece anotasyonlu etiketler `GitTag` nesnelerine soyulabilir. Hafif etiketler (varsayılan) doğrudan `GitCommit` nesnelerine işaret eden `refs/tags/` altında referanslardır.

