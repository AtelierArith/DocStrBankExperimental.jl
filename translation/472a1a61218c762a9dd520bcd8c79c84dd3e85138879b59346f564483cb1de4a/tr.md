```
require(into::Module, module::Symbol)
```

Bu fonksiyon, bir modül `Main` içinde zaten tanımlı değilse [`using`](@ref) / [`import`](@ref) uygulamasının bir parçasıdır. Ayrıca, bir modül daha önce yüklenip yüklenmediğine bakılmaksızın, bir modülü yeniden yüklemeyi zorlamak için doğrudan çağrılabilir (örneğin, etkileşimli olarak kütüphaneler geliştirirken).

Her aktif düğümde, `Main` modülünün bağlamında bir kaynak dosyası yükler ve dosyalar için standart konumları arar. `require`, üst düzey bir işlem olarak kabul edilir, bu nedenle mevcut `include` yolunu ayarlar ancak dosyaları aramak için kullanmaz (bkz. [`include`](@ref) için yardım). Bu fonksiyon genellikle kütüphane kodunu yüklemek için kullanılır ve paketleri yüklemek için `using` tarafından örtük olarak çağrılır.

Dosyaları ararken, `require` önce global dizi [`LOAD_PATH`](@ref) içinde paket kodunu arar. `require`, macOS ve Windows gibi büyük/küçük harf duyarsız dosya sistemlerine sahip olanlar da dahil olmak üzere tüm platformlarda büyük/küçük harf duyarlıdır.

Kod yükleme ile ilgili daha fazla ayrıntı için, [modüller](@ref modules) ve [paralel hesaplama](@ref code-availability) konularındaki kılavuz bölümlerine bakın.
