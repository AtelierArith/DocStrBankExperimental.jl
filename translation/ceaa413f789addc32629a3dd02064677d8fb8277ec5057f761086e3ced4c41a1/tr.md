```
LibGit2.RebaseOptions
```

`git_rebase_options` yapısını karşılar.

Alanlar şunları temsil eder:

  * `version`: kullanılan yapının versiyonu, bu daha sonra değişirse. Şu anda her zaman `1`.
  * `quiet`: rebase ile ilgilenen/çalışan diğer git istemcilerine rebase'in "sessizce" yapılması gerektiğini bildirir. Eşdüzgünlük için kullanılır. Varsayılan `1`'dir.
  * `inmemory`: bellek içi bir rebase başlatır. Rebase üzerinde çalışan çağrıcılar adımları geçebilir ve değişiklikleri kaydedebilir, ancak HEAD'i geri alıp depoyu güncelleyemez. [`workdir`](@ref) değiştirilmez. Sadece 0.24.0 veya daha yeni libgit2 sürümlerinde mevcuttur.
  * `rewrite_notes_ref`: rebase tamamlandığında commit notlarını yeniden yazmak için kullanılacak notların referansının adı.
  * `merge_opts`: her rebase adımında ağaçların nasıl birleştirileceğini kontrol eden birleştirme seçenekleri. Sadece 0.24.0 veya daha yeni libgit2 sürümlerinde mevcuttur.
  * `checkout_opts`: rebase'i başlatırken, adım adım geçerken ve iptal ederken dosyaları yazmak için checkout seçenekleri. Daha fazla bilgi için [`CheckoutOptions`](@ref) bölümüne bakın.
