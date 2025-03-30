```
GC.enable(on::Bool)
```

Çöp toplamanın etkin olup olmadığını bir boolean argümanı kullanarak kontrol edin (`true` etkin, `false` devre dışı). Önceki GC durumunu döndürün.

!!! uyarı     Çöp toplamanın devre dışı bırakılması yalnızca dikkatle kullanılmalıdır, çünkü bellek kullanımının sınırsız bir şekilde artmasına neden olabilir.
