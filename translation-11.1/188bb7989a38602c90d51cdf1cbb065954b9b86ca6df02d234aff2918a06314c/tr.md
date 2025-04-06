```
@timev expr
@timev "açıklama" expr
```

Bu, `@time` makrosunun ayrıntılı bir versiyonudur. Öncelikle `@time` ile aynı bilgileri yazdırır, ardından sıfırdan farklı bellek tahsis sayıcılarını gösterir ve ardından ifadenin değerini döndürür.

Zaman raporundan önce yazdırmak için isteğe bağlı bir açıklama dizesi sağlayabilirsiniz.

!!! uyumluluk "Julia 1.8"
    Açıklama ekleme seçeneği Julia 1.8'de tanıtılmıştır.


Ayrıca [`@time`](@ref), [`@timed`](@ref), [`@elapsed`](@ref), [`@allocated`](@ref) ve [`@allocations`](@ref) ile de bakabilirsiniz.

```julia-repl
julia> x = rand(10,10);

julia> @timev x * x;
  0.546770 saniye (2.20 M tahsis: 116.632 MiB, %4.23 gc süresi, %99.94 derleme süresi)
geçen süre (ns): 546769547
gc süresi (ns):      23115606
tahsis edilen bayt:   122297811
havuz tahsisleri:       2197930
havuz dışı GC tahsisleri:1327
malloc() çağrıları:    36
realloc() çağrıları:   5
GC duraklamaları:         3

julia> @timev x * x;
  0.000010 saniye (1 tahsis: 896 bayt)
geçen süre (ns): 9848
tahsis edilen bayt:   896
havuz tahsisleri:       1
```
