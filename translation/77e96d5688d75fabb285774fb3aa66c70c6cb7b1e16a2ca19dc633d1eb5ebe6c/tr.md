```
@async
```

Bir ifadeyi [`Task`](@ref) içine sarın ve yerel makinenin zamanlayıcı kuyruğuna ekleyin.

Değerler, `$` aracılığıyla `@async` içine interpolasyon yapılabilir; bu, değeri doğrudan oluşturulan alt kapanıma kopyalar. Bu, bir değişkenin *değerini* eklemenizi sağlar ve asenkron kodu mevcut görevdeki değişkenin değerindeki değişikliklerden izole eder.

!!! warning
    `@async` yerine her zaman `Threads.@spawn` kullanmanız şiddetle tavsiye edilir **paralellik gereksinimi olmasa bile**, özellikle kamuya açık dağıtılan kütüphanelerde. Bunun nedeni, `@async` kullanımının, Julia'nın mevcut uygulamasında *ebeveyn* görevlerin işçi iş parçacıkları arasında taşınmasını devre dışı bırakmasıdır. Bu nedenle, bir kütüphane fonksiyonunda `@async` kullanımının görünüşte masum bir şekilde, kullanıcı uygulamalarının çok farklı bölümlerinin performansı üzerinde büyük bir etkisi olabilir.


!!! compat "Julia 1.4"
    `$` aracılığıyla değerlerin interpolasyonu, Julia 1.4 itibarıyla mevcuttur.

