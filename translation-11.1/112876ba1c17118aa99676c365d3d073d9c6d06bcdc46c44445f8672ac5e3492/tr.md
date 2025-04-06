```
ssh_pub_key_path() :: String
```

`ssh_pub_key_path()` fonksiyonu, SSH bağlantıları için kullanılacak olan SSH genel anahtar dosyasının yolunu döndürür. Eğer `SSH_PUB_KEY_PATH` ortam değişkeni ayarlanmışsa, o değeri döndürecektir. Eğer bu ayarlanmamışsa ama `SSH_KEY_PATH` ayarlanmışsa, o yolun sonuna `.pub` ekleyerek döndürecektir. Eğer ikisi de ayarlanmamışsa, varsayılan olarak

```
joinpath(ssh_dir(), ssh_key_name() * ".pub")
```

değerini döndürür. Bu varsayılan değer, `SSH_DIR` ve `SSH_KEY_NAME` ortam değişkenlerine bağlıdır.
