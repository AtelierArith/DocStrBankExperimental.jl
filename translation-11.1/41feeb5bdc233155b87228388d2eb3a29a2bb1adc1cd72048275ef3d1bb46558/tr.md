```
Iterators.reverse(itr)
```

Bir iterator `itr` verildiğinde, `reverse(itr)` aynı koleksiyon üzerinde ancak ters sırada bir iterator döndürür. Bu iterator "tembel"dir; tersine çevirmek için koleksiyonun bir kopyasını oluşturmaz; bunun için hevesli bir uygulama için [`Base.reverse`](@ref) kısmına bakın.

(Varsayılan olarak, bu `itr`'yi saran bir `Iterators.Reverse` nesnesi döndürür; bu nesne, ilgili [`iterate`](@ref) yöntemleri tanımlıysa yine de yineleyebilir, ancak bazı `itr` türleri daha özel `Iterators.reverse` davranışlarını uygulayabilir.)

Tüm iterator türleri `T` ters sıra ile yinelemeyi desteklemez. Eğer `T` desteklemiyorsa, `Iterators.reverse(itr::T)` üzerinde yineleme yapmak, `Iterators.Reverse{T}` için eksik `iterate` yöntemleri nedeniyle bir [`MethodError`](@ref) fırlatır. (Bu yöntemleri uygulamak için, orijinal iterator `itr::T`, `r::Iterators.Reverse{T}` nesnesinden `r.itr` ile elde edilebilir; daha genel olarak, `Iterators.reverse(r)` kullanılabilir.)

# Örnekler

```jldoctest
julia> foreach(println, Iterators.reverse(1:5))
5
4
3
2
1
```
