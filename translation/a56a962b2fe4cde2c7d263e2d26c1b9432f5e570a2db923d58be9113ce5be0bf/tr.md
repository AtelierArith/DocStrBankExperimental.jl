```
varinfo(m::Module=Main, pattern::Regex=r""; all=false, imported=false, recursive=false, sortby::Symbol=:name, minsize::Int=0)
```

Bir modüldeki genel değişkenler hakkında bilgi veren bir markdown tablosu döndürün, isteğe bağlı olarak `pattern` ile eşleşenlerle sınırlı.

Hafıza tüketimi tahmini, nesnenin iç yapısının boyutu için yaklaşık bir alt sınırdır.

  * `all` : modülde tanımlanan kamuya açık olmayan nesneleri, kullanımdan kaldırılmış nesneleri ve derleyici tarafından üretilen nesneleri de listeleyin.
  * `imported` : diğer modüllerden açıkça içe aktarılan nesneleri de listeleyin.
  * `recursive` : alt modüllerdeki nesneleri de dahil edin, her birinde aynı ayarları gözlemleyin.
  * `sortby` : sonuçları sıralamak için kullanılacak sütun. Seçenekler `:name` (varsayılan), `:size` ve `:summary`'dır.
  * `minsize` : yalnızca boyutu en az `minsize` bayt olan nesneleri dahil eder. Varsayılan `0`'dır.

`varinfo` çıktısı yalnızca görüntüleme amaçlıdır. Daha genel manipülasyonlar için bir modülde tanımlanan sembollerin bir dizisini almak üzere [`names`](@ref) fonksiyonuna da bakın.
