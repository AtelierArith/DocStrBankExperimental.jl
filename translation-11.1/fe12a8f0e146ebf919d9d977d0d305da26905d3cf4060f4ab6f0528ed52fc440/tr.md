```
GC.safepoint()
```

Programda çöp toplamanın çalışabileceği bir noktayı ekler. Bu, bazı iş parçacıklarının bellek ayırdığı (ve bu nedenle GC'yi çalıştırması gerekebileceği) ancak diğer iş parçacıklarının yalnızca basit işlemler yaptığı (ayırma, görev geçişleri veya G/Ç yok) çok iş parçacıklı programlarda nadir durumlarda yararlı olabilir. Ayırma yapmayan iş parçacıklarında bu işlevi periyodik olarak çağırmak, çöp toplamanın çalışmasına izin verir.

!!! compat "Julia 1.4"
    Bu işlev, Julia 1.4 itibarıyla mevcuttur.

