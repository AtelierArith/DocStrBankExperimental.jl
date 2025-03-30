```
ca_roots_path() :: String
```

`ca_roots_path()` fonksiyonu, `ca_roots()` fonksiyonuna benzer, ancak her zaman PEM kodlu sertifika otoritesi köklerinin bir dosya veya dizin yolunu döndürür. Windows veya macOS gibi dosya sisteminde sistem kök sertifikalarının saklanmadığı bir sistemde çağrıldığında, şu anda Julia ile birlikte paketlenmiş kök sertifikalarının setinin yolunu döndürecektir. (Gelecekte, bu fonksiyon sistemden kök sertifikalarını çıkartıp, yolunun döndürüleceği bir dosyaya kaydedebilir.)

TLS kullanan bir kütüphaneyi sistem sertifikalarını kullanacak şekilde yapılandırmak mümkünse, bu genellikle tercih edilir: yani, sistem sertifikalarının kullanılacağını belirtmek için `nothing` döndüren `ca_roots()` kullanmak daha iyidir. `ca_roots_path()` fonksiyonu yalnızca kök sertifikaları için bir dosya veya dizin yoluna *gereksinim duyan* kütüphaneleri yapılandırırken kullanılmalıdır.

`ca_roots_path()` tarafından döndürülen varsayılan değer, `JULIA_SSL_CA_ROOTS_PATH`, `SSL_CERT_DIR` veya `SSL_CERT_FILE` ortam değişkenlerini ayarlayarak geçersiz kılınabilir; bu durumda bu fonksiyon, ayarlanmış olan bu değişkenlerden ilki ne olursa olsun, her zaman o değişkenin değerini döndürecektir (yolun var olup olmadığına bakılmaksızın). `JULIA_SSL_CA_ROOTS_PATH` boş bir dizeye ayarlandığında, diğer değişkenler göz ardı edilir (sanki ayarlanmamış gibi); diğer değişkenler boş bir dizeye ayarlandığında, ayarlanmamış gibi davranırlar.
