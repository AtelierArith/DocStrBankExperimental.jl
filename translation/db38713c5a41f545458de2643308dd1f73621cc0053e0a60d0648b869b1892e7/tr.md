```
gebal!(iş, A) -> (ilo, ihi, ölçek)
```

Matris `A`'yı özdeğer sistemi veya Schur faktorizasyonu hesaplamadan önce dengeleyin. `iş`, `N` (`A` sıralanmayacak veya ölçeklenmeyecek), `P` (`A` yalnızca sıralanacak), `S` (`A` yalnızca ölçeklenecek) veya `B` (`A` hem sıralanacak hem de ölçeklenecek) olanlardan biri olabilir. `A`'yı yerinde değiştirir ve `ilo`, `ihi` ve `ölçek` döner. Sıralama etkinleştirildiyse, `A[i,j] = 0` eğer `j > i` ve `1 < j < ilo` veya `j > ihi` ise. `ölçek`, gerçekleştirilen ölçekleme/sıralamalar hakkında bilgi içerir.
