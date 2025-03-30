```
redisplay(x)
redisplay(d::AbstractDisplay, x)
redisplay(mime, x)
redisplay(d::AbstractDisplay, mime, x)
```

Varsayılan olarak, `redisplay` fonksiyonları basitçe [`display`](@ref) çağrısını yapar. Ancak, bazı görüntüleme arka uçları mevcut `x` görüntüsünü (varsa) değiştirmek için `redisplay`'i geçersiz kılabilir. `redisplay` kullanmak, arka uca `x`'in birkaç kez yeniden görüntülenebileceği konusunda bir ipucu verir ve arka uç, görüntülemeyi (örneğin) bir sonraki etkileşimli isteme kadar ertelemeyi seçebilir.
