```
LibGit2.FetchOptions
```

[`git_fetch_options`](https://libgit2.org/libgit2/#HEAD/type/git_fetch_options) yapısına karşılık gelir.

Alanlar şunları temsil eder:

  * `version`: kullanılan yapının versiyonu, bu daha sonra değişirse. Şu anda her zaman `1`.
  * `callbacks`: fetch sırasında kullanılacak uzak geri çağrılar.
  * `prune`: fetch'ten sonra bir temizleme yapılıp yapılmayacağı. Varsayılan, `GitConfig`'ten gelen ayarı kullanmaktır.
  * `update_fetchhead`: fetch'ten sonra [`FetchHead`](@ref) güncellenip güncellenmeyeceği. Varsayılan, güncellemeyi gerçekleştirmektir, bu normal git davranışıdır.
  * `download_tags`: uzakta bulunan etiketlerin indirilip indirilmeyeceği. Varsayılan, sunucudan zaten indirilen nesneler için etiketleri talep etmektir.
  * `proxy_opts`: bir proxy üzerinden uzak bağlantı kurmak için seçenekler. Sadece 0.25.0 veya daha yeni libgit2 sürümlerinde mevcuttur.
  * `custom_headers`: fetch için gereken ek başlıklar. Sadece 0.24.0 veya daha yeni libgit2 sürümlerinde mevcuttur.
