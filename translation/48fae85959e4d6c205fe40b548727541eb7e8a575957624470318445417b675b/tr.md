```
ssh_key_pass() :: String
```

`ssh_key_pass()` fonksiyonu, ayarlanmışsa `SSH_KEY_PASS` ortam değişkeninin değerini döndürür veya ayarlanmamışsa `nothing` döndürür. Gelecekte, bu, güvenli sistem depolaması gibi diğer yollarla bir şifre bulma yeteneğine sahip olabilir, bu nedenle bir SSH özel anahtarını şifrelemek için bir şifreye ihtiyaç duyan paketler, ortam değişkenini doğrudan kontrol etmek yerine bu API'yi kullanmalıdır, böylece eklendiklerinde bu yetenekleri otomatik olarak kazanırlar.
