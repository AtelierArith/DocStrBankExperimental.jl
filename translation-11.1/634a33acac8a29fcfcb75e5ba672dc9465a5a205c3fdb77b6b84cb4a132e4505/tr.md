```
sygvd!(itype, jobz, uplo, A, B) -> (w, A, B)
```

Genelleştirilmiş özdeğerleri (`jobz = N`) veya özdeğerler ve özvektörleri (`jobz = V`) simetrik matris `A` ve simetrik pozitif-tam matris `B` için bulur. Eğer `uplo = U` ise, `A` ve `B`'nin üst üçgenleri kullanılır. Eğer `uplo = L` ise, `A` ve `B`'nin alt üçgenleri kullanılır. Eğer `itype = 1` ise, çözülmesi gereken problem `A * x = lambda * B * x`'dir. Eğer `itype = 2` ise, çözülmesi gereken problem `A * B * x = lambda * x`'dir. Eğer `itype = 3` ise, çözülmesi gereken problem `B * A * x = lambda * x`'dir.
