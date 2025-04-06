```
ssh_known_hosts_files() :: Vector{String}
```

`ssh_known_hosts_files()` fonksiyonu, SSH bağlantıları için uzak sunucuların kimliklerini belirlerken kullanılacak SSH bilinen anahtar dosyalarının yollarının bir vektörünü döndürür. Varsayılan olarak bu fonksiyon şunları döndürür:

```
[joinpath(ssh_dir(), "known_hosts"), bundled_known_hosts]
```

burada `bundled_known_hosts`, bu paketle birlikte gelen (github.com ve gitlab.com için bilinen anahtarları içeren) bir bilinen anahtar dosyasının kopyasının yoludur. Ancak, `SSH_KNOWN_HOSTS_FILES` ortam değişkeni ayarlanmışsa, değeri `:` karakterine (veya Windows'ta `;` karakterine) göre yollar olarak ayrılır ve bu yolların vektörü döndürülür. Bu vektörün herhangi bir bileşeni boşsa, varsayılan bilinen anahtar yollarına genişletilir.

`ssh_known_hosts_files()` kullanan paketler, ideal olarak, ana bilgisayar adı ve anahtar türlerini karşılaştırarak eşleşen girişleri aramalıdır; eşleşen ilk giriş, ana bilgisayarın kesin kimliği olarak kabul edilir. Çağrıcı anahtar türünü karşılaştıramazsa (örneğin, çünkü hashlenmişse), yukarıdaki algoritmayı, her dosyada bir ana bilgisayar için tüm eşleşen girişleri arayarak yaklaşık olarak uygulamalıdır: bir dosyada bir ana bilgisayar için herhangi bir giriş varsa, bunlardan biri eşleşmelidir; çağrıcı, daha önceki bir dosyada söz konusu ana bilgisayar için hiçbir giriş yoksa, daha fazla bilinen anahtar dosyalarında aramaya devam etmelidir.
