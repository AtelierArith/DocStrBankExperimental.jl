```
SubArray{T,N,P,I,L} <: AbstractArray{T,N}
```

`N`-boyutlu bir üst diziye (tipi `P`) bir ana diziye bakış, bir indeksler demeti (tipi `I`) ile kısıtlanmış bir eleman tipi `T` ile. `L`, hızlı lineer indekslemeyi destekleyen türler için doğrudur ve aksi takdirde yanlıştır.

`SubArray`'ları [`view`](@ref) fonksiyonu kullanarak oluşturun.
