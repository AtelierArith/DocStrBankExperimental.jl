```
@simd
```

Bir `for` döngüsünü, derleyicinin döngü yeniden sıralamasına izin vermek için ekstra özgürlükler almasına olanak tanımak üzere not edin.

!!! uyarı     Bu özellik deneysel olup, Julia'nın gelecekteki sürümlerinde değişebilir veya kaybolabilir. `@simd` makrosunun yanlış kullanımı beklenmedik sonuçlara yol açabilir.

`@simd for` döngüsünde yinelemeli nesne bir boyutlu bir aralık olmalıdır. `@simd` kullanarak, döngünün birkaç özelliğini beyan ediyorsunuz:

  * İterasyonların rastgele veya örtüşen sırada yürütülmesi güvenlidir, özellikle azaltma değişkenleri için özel dikkate alınmalıdır.
  * Azaltma değişkenleri üzerindeki kayan nokta işlemleri yeniden sıralanabilir veya birleştirilebilir, bu da `@simd` olmadan farklı sonuçlar doğurabilir.

Birçok durumda, Julia, `@simd` kullanmadan iç `for` döngülerini otomatik olarak vektörleştirebilir. `@simd` kullanmak, derleyiciye daha fazla durumlarda bunu mümkün kılmak için biraz ekstra esneklik verir. Her iki durumda da, iç döngünüzün vektörleştirmeye izin vermek için aşağıdaki özelliklere sahip olması gerekir:

  * Döngü en içteki döngü olmalıdır.
  * Döngü gövdesi düz hat kodu olmalıdır. Bu nedenle, tüm dizi erişimleri için şu anda [`@inbounds`](@ref) gereklidir. Derleyici, tüm operandları koşulsuz olarak değerlendirmek güvenli olduğunda kısa `&&`, `||` ve `?:` ifadelerini düz hat koduna dönüştürebilir. Döngüde `?:` yerine [`ifelse`](@ref) fonksiyonunu kullanmayı düşünün, eğer bunu yapmak güvenliyse.
  * Erişimlerin bir adım deseni olmalı ve "toplama" (rastgele indeks okumaları) veya "dağıtma" (rastgele indeks yazmaları) olamaz.
  * Adım birim adım olmalıdır.

!!! not
    `@simd`, varsayılan olarak döngünün tamamen döngü taşınan bellek bağımlılıklarından özgür olduğunu beyan etmez; bu, genel kodda kolayca ihlal edilebilecek bir varsayımdır. Genel olmayan kod yazıyorsanız, `@simd ivdep for ... end` kullanarak şunları da beyan edebilirsiniz:


  * Döngü taşınan bellek bağımlılıkları yoktur.
  * Hiçbir yineleme, ileriye doğru ilerlemek için önceki bir yinelemeyi beklemez.
