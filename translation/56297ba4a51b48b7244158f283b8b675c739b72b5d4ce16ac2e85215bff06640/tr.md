```
Base.@constprop ayar [ex]
```

Açıklamalı fonksiyon için interprosedürel sabit yayılma modunu kontrol edin.

İki `ayar` desteklenmektedir:

  * `Base.@constprop :aggressive [ex]`: sabit yayılmayı agresif bir şekilde uygulayın. Dönüş türünün argümanların değerine bağlı olduğu bir yöntem için, bu ek derleme süresi maliyeti karşılığında iyileştirilmiş çıkarım sonuçları sağlayabilir.
  * `Base.@constprop :none [ex]`: sabit yayılmayı devre dışı bırakın. Bu, Julia'nın aksi takdirde sabit yayılma için değerli görebileceği fonksiyonlar için derleme sürelerini azaltabilir. Yaygın durumlar, `Bool` veya `Symbol` değerli argümanlar veya anahtar kelime argümanları olan fonksiyonlardır.

`Base.@constprop`, bir fonksiyon tanımından hemen önce veya bir fonksiyon gövdesi içinde uygulanabilir.

```julia
# uzun biçim tanımını not edin
Base.@constprop :aggressive function longdef(x)
    ...
end

# kısa biçim tanımını not edin
Base.@constprop :aggressive shortdef(x) = ...

# bir `do` bloğunun oluşturduğu anonim fonksiyonu not edin
f() do
    Base.@constprop :aggressive
    ...
end
```

!!! uyum "Julia 1.10"
    Bir fonksiyon gövdesi içinde kullanım en az Julia 1.10 gerektirir.

