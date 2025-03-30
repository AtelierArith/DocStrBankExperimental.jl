```
Random.default_rng() -> rng
```

Varsayılan küresel rastgele sayı üreteci (RNG) döndürülür; bu, açık bir RNG sağlanmadığında `rand` ile ilgili işlevler tarafından kullanılır.

`Random` modülü yüklendiğinde, varsayılan RNG *rastgele* bir şekilde tohumlanır; bu, her yeni julia oturumu başlatıldığında, `rand()`'ın ilk çağrısının farklı bir sonuç üretmesi anlamına gelir, aksi takdirde `seed!(seed)` çağrılmadıkça.

Thread güvenlidir: farklı thread'ler, `default_rng()` üzerinde `rand` ile ilgili işlevleri güvenli bir şekilde eşzamanlı olarak çağırabilir, örneğin `rand(default_rng())`.

!!! note
    Varsayılan RNG'nin türü bir uygulama ayrıntısıdır. Farklı Julia sürümleri arasında, varsayılan RNG'nin her zaman aynı türde olmasını veya belirli bir tohum için aynı rastgele sayı akışını üretmesini beklememelisiniz.


!!! compat "Julia 1.3"
    Bu işlev Julia 1.3'te tanıtılmıştır.

