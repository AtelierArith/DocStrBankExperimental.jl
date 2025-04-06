```
ca_roots() :: Union{Nothing, String}
```

`ca_roots()` fonksiyonu, çağırana PEM kodlu sertifika otoritesi köklerinin dosyasını veya dizinini nerede bulacağını söyler. Varsayılan olarak, sistemin yerleşik sertifika doğrulama mekanizmasını kullanarak ana bilgisayarları doğrulama yeteneğine sahip yerleşik TLS motorlarına sahip Windows ve macOS gibi sistemlerde, bu fonksiyon `nothing` döndürecektir. Klasik UNIX sistemlerinde (macOS hariç), kök sertifikaları genellikle `/etc` dizininde bir dosyada saklanır: mevcut UNIX sisteminin yaygın yerleri aranacak ve bu yollardan biri mevcutsa, o yol döndürülecektir; eğer bu tipik kök sertifika yollarından hiçbiri mevcut değilse, o zaman Julia ile birlikte gelen kök sertifikalarının setinin yolu döndürülecektir.

`ca_roots()` tarafından döndürülen varsayılan değer, `JULIA_SSL_CA_ROOTS_PATH`, `SSL_CERT_DIR` veya `SSL_CERT_FILE` ortam değişkenlerini ayarlayarak geçersiz kılınabilir; bu durumda bu fonksiyon, ayarlanmış olan bu değişkenlerden ilki ne olursa olsun, her zaman o değişkenin değerini döndürecektir (yol mevcut olup olmadığına bakılmaksızın). `JULIA_SSL_CA_ROOTS_PATH` boş bir dizeye ayarlandığında, diğer değişkenler göz ardı edilir (sanki ayarlanmamış gibi); diğer değişkenler boş bir dizeye ayarlandığında, ayarlanmamış gibi davranırlar.
