```
hetrf!(uplo, A) -> (A, ipiv, info)
```

Hermit matris `A`'nın Bunch-Kaufman faktorizasyonunu hesaplar. Eğer `uplo = U` ise, `A`'nın üst yarısı saklanır. Eğer `uplo = L` ise, alt yarısı saklanır.

Faktorizasyon ile üzerine yazılmış `A`, bir pivot vektörü `ipiv` ve pozitif bir tam sayı olan hata kodu `info` döner. Eğer `info` pozitifse, matris tekil olup faktorizasyonun diyagonal kısmı `info` konumunda tam olarak sıfırdır.
