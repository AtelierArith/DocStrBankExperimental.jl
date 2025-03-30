```
LibGit2.ProxyOptions
```

Proxy üzerinden bağlantı kurmak için seçenekler.

[`git_proxy_options`](https://libgit2.org/libgit2/#HEAD/type/git_proxy_options) yapısıyla eşleşir.

Alanlar şunları temsil eder:

  * `version`: kullanılan yapının versiyonu, bu daha sonra değişirse. Şu anda her zaman `1`.
  * `proxytype`: kullanılacak proxy türü için bir `enum`. [`git_proxy_t`](https://libgit2.org/libgit2/#HEAD/type/git_proxy_t) içinde tanımlıdır. Karşılık gelen Julia enum'u `GIT_PROXY` ve değerleri şunlardır:

      * `PROXY_NONE`: bağlantıyı bir proxy üzerinden denemeyin.
      * `PROXY_AUTO`: git yapılandırmasından proxy yapılandırmasını anlamaya çalışın.
      * `PROXY_SPECIFIED`: bu yapının `url` alanında verilen URL'yi kullanarak bağlanın.

    Varsayılan, proxy türünü otomatik olarak tespit etmektir.
  * `url`: proxy'nin URL'si.
  * `credential_cb`: uzaktan bağlantı için kimlik doğrulaması gerekiyorsa çağrılacak bir geri çağırma fonksiyonuna işaretçi.
  * `certificate_cb`: sertifika doğrulaması başarısız olursa çağrılacak bir geri çağırma fonksiyonuna işaretçi. Bu, kullanıcının bağlantıya devam edip etmeyeceğine karar vermesini sağlar. Fonksiyon `1` dönerse, bağlantıya izin verilecektir. `0` dönerse, bağlantıya izin verilmeyecektir. Hata döndürmek için negatif bir değer kullanılabilir.
  * `payload`: iki geri çağırma fonksiyonuna sağlanacak yük.

# Örnekler

```julia-repl
julia> fo = LibGit2.FetchOptions(
           proxy_opts = LibGit2.ProxyOptions(url = Cstring("https://my_proxy_url.com")))

julia> fetch(remote, "master", options=fo)
```
