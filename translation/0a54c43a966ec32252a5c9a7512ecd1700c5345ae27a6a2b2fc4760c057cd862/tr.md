```
syevd!(jobz, uplo, A)
```

Simetrik bir matris `A`'nın özdeğerlerini (`jobz = N`) veya özdeğerler ve özvektörlerini (`jobz = V`) bulur. Eğer `uplo = U` ise, `A`'nın üst üçgeni kullanılır. Eğer `uplo = L` ise, `A`'nın alt üçgeni kullanılır.

`syev!` tarafından kullanılan QR iterasyonu veya `syevr!` tarafından kullanılan çoklu nispeten sağlam temsiller yerine, böl ve fethet yöntemini kullanır. Farklı yöntemlerin doğruluğu ve performans karşılaştırması için James W. Demmel ve diğerleri, SIAM J. Sci. Comput. 30, 3, 1508 (2008) referansına bakın.
