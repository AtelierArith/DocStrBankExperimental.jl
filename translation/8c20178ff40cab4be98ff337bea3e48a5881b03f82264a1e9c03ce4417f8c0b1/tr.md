```
withenv(f, kv::Pair...)
```

`f`'yi, sıfır veya daha fazla `"var"=>val` argümanı `kv` ile geçici olarak değiştirilmiş (yerine geçmek yerine `setenv` gibi) bir ortamda çalıştırır. `withenv`, genellikle `withenv(kv...) do ... end` sözdizimi aracılığıyla kullanılır. Bir ortam değişkenini (eğer ayarlanmışsa) geçici olarak kaldırmak için `nothing` değeri kullanılabilir. `withenv` döndüğünde, orijinal ortam geri yüklenmiştir.

!!! uyarı     Ortamı değiştirmek, iş parçacığı güvenli değildir. Ana süreçten farklı bir ortamla dış komutlar çalıştırmak için, `withenv` yerine [`addenv`](@ref) kullanmayı tercih edin.
