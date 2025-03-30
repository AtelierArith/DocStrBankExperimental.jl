```
sizehint!(s, n; first::Bool=false, shrink::Bool=true) -> s
```

Koleksiyon `s`'nin en az `n` eleman için kapasite ayırmasını önerir. Yani, `s`'ye birçok değer ekleyeceğinizi düşünüyorsanız, bunu önceden bir kez yaparak artan yeniden tahsisat maliyetinden kaçınabilirsiniz; bu performansı artırabilir.

Eğer `first` `true` ise, o zaman ek alan koleksiyonun başlangıcından önce ayrılır. Bu şekilde, `push!` yerine `pushfirst!` çağrıları daha hızlı hale gelebilir. Bu anahtar kelimeyi sağlamak, koleksiyon sıralı değilse veya `pushfirst!` bu koleksiyon için desteklenmiyorsa bir hataya neden olabilir.

Eğer `shrink=true` (varsayılan), koleksiyonun mevcut kapasitesi `n`'den büyükse kapasitesi azaltılabilir.

Ayrıca [`resize!`](@ref) bakınız.

# Performans modeli hakkında notlar

`sizehint!` destekleyen türler için,

1. `push!` ve `append!` yöntemleri genellikle (ancak zorunlu değildir) ek depolama önceden ayırabilir. `Base` içinde uygulanan türler için genellikle bunu yapar, genel bir kullanım durumu için optimize edilmiş bir sezgi kullanarak.
2. `sizehint!` bu ön tahsisi kontrol edebilir. Yine, genellikle `Base` içindeki türler için bunu yapar.
3. `empty!`, bu tür ön tahsisi destekleyen türler için neredeyse maliyetsizdir (ve O(1)).

!!! compat "Julia 1.11"
    `shrink` ve `first` argümanları Julia 1.11'de eklendi.

