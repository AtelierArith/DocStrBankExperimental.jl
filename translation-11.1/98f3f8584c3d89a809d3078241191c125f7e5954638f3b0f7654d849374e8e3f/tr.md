```
partialsortperm(v, k; by=identity, lt=isless, rev=false)
```

Vektör `v`'nin kısmi bir permütasyonunu `I` olarak döndürür, böylece `v[I]` `v`'nin tamamen sıralanmış bir versiyonunun `k` indeksindeki değerlerini döndürür. Eğer `k` bir aralıksa, bir indeks vektörü döndürülür; eğer `k` bir tam sayıysa, tek bir indeks döndürülür. Sıralama, `sort!` ile aynı anahtar kelimeleri kullanarak belirtilir. Permütasyon kararlıdır: eşit elemanların indeksleri artan sırada görünecektir.

Bu fonksiyon, `sortperm(...)[k]` çağrısına eşdeğerdir, ancak daha verimlidir.

# Örnekler

```jldoctest
julia> v = [3, 1, 2, 1];

julia> v[partialsortperm(v, 1)]
1

julia> p = partialsortperm(v, 1:3)
3-element view(::Vector{Int64}, 1:3) with eltype Int64:
 2
 4
 3

julia> v[p]
3-element Vector{Int64}:
 1
 1
 2
```
