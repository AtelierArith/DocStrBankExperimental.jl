```
deepcopy(x)
```

`x`'in derin bir kopyasını oluşturur: her şey özyinelemeli olarak kopyalanır ve tamamen bağımsız bir nesne ortaya çıkar. Örneğin, bir dizinin derin kopyasını almak, içerdiği tüm nesnelerin derin kopyalarını oluşturur ve tutarlı ilişki yapısına sahip yeni bir dizi üretir (örneğin, orijinal dizideki ilk iki eleman aynı nesne ise, yeni dizinin ilk iki elemanı da aynı `deepcopy` edilmiş nesne olacaktır). Bir nesne üzerinde `deepcopy` çağırmak, genellikle onu serileştirmek ve ardından serileştirilmiş halini geri almakla aynı etkiye sahip olmalıdır.

Normalde gerekli olmasa da, kullanıcı tanımlı türler, `deepcopy_internal(x::T, dict::IdDict)` fonksiyonunun özel bir versiyonunu tanımlayarak varsayılan `deepcopy` davranışını geçersiz kılabilir (bu başka bir yerde kullanılmamalıdır), burada `T` özelleştirilecek türdür ve `dict` özyineleme içinde şu ana kadar kopyalanan nesneleri takip eder. Tanım içinde, `deepcopy_internal` yerine `deepcopy` kullanılmalı ve `dict` değişkeni uygun şekilde güncellenmelidir.
