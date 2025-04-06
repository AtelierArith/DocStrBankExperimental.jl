```
LibGit2.CheckoutOptions
```

[`git_checkout_options`](https://libgit2.org/libgit2/#HEAD/type/git_checkout_options) yapısına karşılık gelir.

Alanlar şunları temsil eder:

  * `version`: Kullanımda olan yapının versiyonu, bu daha sonra değişirse. Şu anda her zaman `1`.
  * `checkout_strategy`: Çatışmaların nasıl ele alınacağını ve dosyaların zorla kontrol edilip edilmeyeceğini veya eksik dosyaların yeniden oluşturulup oluşturulmayacağını belirler.
  * `disable_filters`: Sıfırdan farklıysa, CLRF gibi filtreleri uygulamayın (UNIX ve DOS arasındaki dosya satır sonlarını dönüştürmek için).
  * `dir_mode`: Kontrol sırasında yer alan herhangi bir dizin için okuma/yazma/erişim modu. Varsayılan `0755`'tir.
  * `file_mode`: Kontrol sırasında yer alan herhangi bir dosya için okuma/yazma/erişim modu. Varsayılan `0755` veya `0644`, blob'a bağlı olarak.
  * `file_open_flags`: Kontrol sırasında herhangi bir dosyayı açmak için kullanılan bit bayrakları.
  * `notify_flags`: Kullanıcının hangi tür çatışmalar hakkında bilgilendirilmesi gerektiği için bayraklar.
  * `notify_cb`: Bir kontrol çatışması meydana geldiğinde kullanıcıyı bilgilendirmek için isteğe bağlı bir geri çağırma fonksiyonu. Bu fonksiyon sıfırdan farklı bir değer dönerse, kontrol iptal edilecektir.
  * `notify_payload`: Bilgilendirme geri çağırma fonksiyonu için yük.
  * `progress_cb`: Kontrol ilerlemesini göstermek için isteğe bağlı bir geri çağırma fonksiyonu.
  * `progress_payload`: İlerleme geri çağırması için yük.
  * `paths`: Boş değilse, kontrol sırasında hangi yolların aranacağını tanımlar. Boşsa, kontrol deposundaki tüm dosyalar üzerinde gerçekleşecektir.
  * `baseline`: [`workdir`](@ref) için beklenen içerik, bir [`GitTree`](@ref) (işaretçi) içinde yakalanmıştır. Varsayılan, HEAD'deki ağacın durumudur.
  * `baseline_index`: [`workdir`](@ref) için beklenen içerik, bir `GitIndex` (işaretçi) içinde yakalanmıştır. Varsayılan, HEAD'deki indeksin durumudur.
  * `target_directory`: Boş değilse, `workdir` yerine bu dizine kontrol yapın.
  * `ancestor_label`: Çatışma durumunda, ortak ata tarafının adı.
  * `our_label`: Çatışma durumunda, "bizim" tarafımızın adı.
  * `their_label`: Çatışma durumunda, "onların" tarafının adı.
  * `perfdata_cb`: Performans verilerini göstermek için isteğe bağlı bir geri çağırma fonksiyonu.
  * `perfdata_payload`: Performans geri çağırması için yük.
