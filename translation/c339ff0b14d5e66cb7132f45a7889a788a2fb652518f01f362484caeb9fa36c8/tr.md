```
Iterators.filter(flt, itr)
```

Bir predikat fonksiyonu `flt` ve bir iterable nesne `itr` verildiğinde, `flt(x)` koşulunu sağlayan `itr`'nin elemanlarını döndüren bir iterable nesne döner. Orijinal iteratorün sırası korunur.

Bu fonksiyon *tembel*dir; yani, $Θ(1)$ zamanında döneceği ve $Θ(1)$ ek alan kullanacağı garanti edilir ve `filter` çağrısı ile `flt` çağrılmayacaktır. `flt`'ye yapılan çağrılar, döndürülen iterable nesne üzerinde yineleme yapılırken gerçekleştirilecektir. Bu çağrılar önbelleğe alınmaz ve tekrar eden çağrılar, yineleme sırasında yapılacaktır.

!!! uyarı     `filter`'den dönen iterator üzerinde yapılan sonraki *tembel* dönüşümler, `Iterators.reverse` veya `cycle` gibi, `flt` çağrılarını, döndürülen iterable nesne üzerinde toplama veya yineleme yapılana kadar geciktirecektir. Eğer filtre predikatı belirsizse veya döndürdüğü değerler `itr`'nin elemanları üzerindeki yineleme sırasına bağlıysa, tembel dönüşümlerle bileşim, şaşırtıcı davranışlara yol açabilir. Bu istenmiyorsa, ya `flt`'nin saf bir fonksiyon olduğundan emin olun ya da daha fazla dönüşümden önce ara `filter` iteratorlerini toplayın.

Diziler için eager bir filtreleme uygulaması için [`Base.filter`](@ref) kısmına bakın.

# Örnekler

```jldoctest
julia> f = Iterators.filter(isodd, [1, 2, 3, 4, 5])
Base.Iterators.Filter{typeof(isodd), Vector{Int64}}(isodd, [1, 2, 3, 4, 5])

julia> foreach(println, f)
1
3
5

julia> [x for x in [1, 2, 3, 4, 5] if isodd(x)]  # Iterators.filter üzerinde bir jeneratörü toplar
3-element Vector{Int64}:
 1
 3
 5
```
