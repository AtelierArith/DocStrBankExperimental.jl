```
ssh_known_hosts_file() :: String
```

`ssh_known_hosts_file()` fonksiyonu, SSH bağlantıları için uzak sunucuların kimliklerini belirlerken kullanılacak bir SSH bilinen anahtarlar dosyasının tek bir yolunu döndürür. Gerçekten var olan `ssh_known_hosts_files` tarafından döndürülen ilk yolu döndürür. Birden fazla bilinen anahtarlar dosyasında arama yapabilen çağrıcılar, bunun belgelerinde açıklandığı gibi döndürülen tüm dosyalarda anahtar eşleşmeleri aramak için `ssh_known_hosts_files`'ı kullanmalıdır.
