```
ssh_key_path() :: String
```

`ssh_key_path()` fonksiyonu, SSH bağlantıları için kullanılacak SSH özel anahtar dosyasının yolunu döndürür. Eğer `SSH_KEY_PATH` ortam değişkeni ayarlanmışsa, o değeri döndürecektir. Aksi takdirde, varsayılan olarak şunu döndürür:

```
joinpath(ssh_dir(), ssh_key_name())
```

Bu varsayılan değer, `SSH_DIR` ve `SSH_KEY_NAME` ortam değişkenlerine bağlıdır.
