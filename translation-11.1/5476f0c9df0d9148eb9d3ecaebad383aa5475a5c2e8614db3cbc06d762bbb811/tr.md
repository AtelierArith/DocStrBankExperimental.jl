```
syevr!(jobz, range, uplo, A, vl, vu, il, iu, abstol) -> (W, Z)
```

Simetrik bir matris `A`'nın özdeğerlerini (`jobz = N`) veya özdeğerler ve özvektörlerini (`jobz = V`) bulur. Eğer `uplo = U` ise, `A`'nın üst üçgeni kullanılır. Eğer `uplo = L` ise, `A`'nın alt üçgeni kullanılır. Eğer `range = A` ise, tüm özdeğerler bulunur. Eğer `range = V` ise, `(vl, vu]` yarı açık aralığında bulunan özdeğerler bulunur. Eğer `range = I` ise, `il` ve `iu` arasındaki indekslere sahip özdeğerler bulunur. `abstol`, yakınsama için bir tolerans olarak ayarlanabilir.

Özdeğerler `W` içinde ve özvektörler `Z` içinde döndürülür.
