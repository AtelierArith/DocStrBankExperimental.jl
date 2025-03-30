```
tempdir()
```

Geçici dizinin yolunu alır. Windows'ta, `tempdir()` sıralı listede bulunan ilk ortam değişkenini `TMP`, `TEMP`, `USERPROFILE` kullanır. Diğer tüm işletim sistemlerinde, `tempdir()` sıralı listede bulunan ilk ortam değişkenini `TMPDIR`, `TMP`, `TEMP` ve `TEMPDIR` kullanır. Eğer bunlardan hiçbiri bulunamazsa, `"/tmp"` yolu kullanılır.
