```
LibGit2.PushOptions
```

[`git_push_options`](https://libgit2.org/libgit2/#HEAD/type/git_push_options) yapısına karşılık gelir.

Alanlar şunları temsil eder:

  * `version`: kullanılan yapının versiyonu, bu daha sonra değişirse. Şu anda her zaman `1`.
  * `parallelism`: bir paket dosyası oluşturulması gerekiyorsa, bu değişken paket oluşturucu tarafından başlatılacak işçi iş parçacıklarının sayısını ayarlar. `0` ise, paket oluşturucu kullanılacak iş parçacığı sayısını otomatik olarak ayarlayacaktır. Varsayılan `1`'dir.
  * `callbacks`: itme işlemi için kullanılacak geri çağırmalar (örneğin, uzak ile kimlik doğrulama için).
  * `proxy_opts`: yalnızca LibGit2 sürümü `0.25.0` veya daha büyükse geçerlidir. Uzak ile iletişim kurmak için bir proxy kullanma seçeneklerini ayarlar. Daha fazla bilgi için [`ProxyOptions`](@ref) bakın.
  * `custom_headers`: yalnızca LibGit2 sürümü `0.24.0` veya daha büyükse geçerlidir. İtme işlemi için gereken ek başlıklar.
