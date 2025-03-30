```
ssh_key_name() :: String
```

`ssh_key_name()` fonksiyonu, SSH'nin bir bağlantı kurarken kullanması gereken anahtar dosyalarının temel adını döndürür. Bu fonksiyonun doğrudan çağrılması için genellikle bir neden yoktur ve kütüphaneler genellikle tam yolları almak için `ssh_key_path` ve `ssh_pub_key_path` fonksiyonlarını kullanmalıdır. Eğer `SSH_KEY_NAME` ortam değişkeni ayarlanmışsa, bu fonksiyon onu döndürür; aksi takdirde varsayılan olarak `id_rsa` döndürür.
