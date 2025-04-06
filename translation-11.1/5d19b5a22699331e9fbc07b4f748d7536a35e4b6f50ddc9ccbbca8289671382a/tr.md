```
verify_host(url::AbstractString, [transport::AbstractString]) :: Bool
```

`verify_host` fonksiyonu, bir hostun kimliğinin güvenli taşıma yöntemleri (TLS veya SSH gibi) üzerinden iletişim kurarken doğrulanıp doğrulanmayacağını çağırana bildirir. `url` argümanı şunlardan biri olabilir:

1. `proto://` ile başlayan düzgün bir URL
2. `ssh` tarzı çıplak bir host adı veya `user@` ile önceden tanımlanmış bir host adı
3. Yukarıdaki gibi bir `scp` tarzı host, ardından `:` ve bir yol konumu

Her durumda, host adı kısmı ayrıştırılır ve doğrulama yapılıp yapılmayacağı kararı yalnızca host adına dayanarak verilir, giriş URL'sinin başka bir yönü dikkate alınmaz. Özellikle, URL'nin protokolü önemli değildir (aşağıda daha fazla bilgi).

`transport` argümanı, sorgunun hangi tür taşıma ile ilgili olduğunu belirtir. Şu anda bilinen değerler `SSL`/`ssl` (takma adı `TLS`/`tls`) ve `SSH`/`ssh`dir. Eğer taşıma belirtilmezse, sorgu yalnızca host adının taşıma ne olursa olsun doğrulanmaması gerektiği durumunda `true` dönecektir.

Host adı, `transport` sağlanıp sağlanmadığına ve değerine bağlı olarak ilgili ortam değişkenlerindeki host desenleriyle eşleştirilir:

  * `JULIA_NO_VERIFY_HOSTS` — herhangi bir taşıma için doğrulanmaması gereken hostlar
  * `JULIA_SSL_NO_VERIFY_HOSTS` — SSL/TLS için doğrulanmaması gereken hostlar
  * `JULIA_SSH_NO_VERIFY_HOSTS` — SSH için doğrulanmaması gereken hostlar
  * `JULIA_ALWAYS_VERIFY_HOSTS` — her zaman doğrulanması gereken hostlar

Bu değişkenlerin her birinin değerleri, aşağıdaki sözdizimine sahip host adı desenlerinin virgülle ayrılmış bir listesidir — her desen `.` ile parçalara ayrılır ve her parça aşağıdakilerden biri olmalıdır:

1. Bir veya daha fazla ASCII harfi, rakam, tire veya alt çizgi içeren bir literal alan adı bileşeni (teknik olarak yasal bir host adı parçası değildir, ancak bazen kullanılır). Bir literal alan adı bileşeni yalnızca kendisiyle eşleşir.
2. `**`, sıfır veya daha fazla alan adı bileşenini eşleştirir.
3. `*`, herhangi bir alan adı bileşenini eşleştirir.

Bir host adını bu değişkenlerden birindeki desen listesiyle eşleştirirken, host adı `.` ile bileşenlere ayrılır ve bu kelime dizisi desenle eşleştirilir: bir literal desen, o değere sahip bir host adı bileşeniyle tam olarak eşleşir; bir `*` deseni, herhangi bir değere sahip bir host adı bileşeniyle tam olarak eşleşir; bir `**` deseni, herhangi bir sayıda host adı bileşeniyle eşleşir. Örneğin:

  * `**` herhangi bir host adını eşleştirir
  * `**.org` `.org` üst düzey alanındaki herhangi bir host adını eşleştirir
  * `example.com` yalnızca tam olarak `example.com` host adını eşleştirir
  * `*.example.com` `api.example.com` ile eşleşir ancak `example.com` veya `v1.api.example.com` ile eşleşmez
  * `**.example.com` `example.com` dahil olmak üzere `example.com` altındaki herhangi bir alanı, `api.example.com` ve `v1.api.example.com` ile eşleştirir
