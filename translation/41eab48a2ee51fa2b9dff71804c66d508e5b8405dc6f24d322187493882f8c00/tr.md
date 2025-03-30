```
Timer(delay; interval = 0)
```

Görevleri uyandıran bir zamanlayıcı oluşturun (zamanlayıcı nesnesinde [`wait`](@ref) çağrılarak).

Bekleyen görevler, en az `delay` saniyelik bir başlangıç gecikmesinden sonra uyandırılır ve ardından en az `interval` saniye geçtikten sonra tekrar uyandırılır. Eğer `interval` `0` ise, zamanlayıcı yalnızca bir kez tetiklenir. Zamanlayıcı kapatıldığında ([`close`](@ref) ile) bekleyen görevler bir hata ile uyandırılır. Zamanlayıcının hala aktif olup olmadığını kontrol etmek için [`isopen`](@ref) kullanın.

!!! not
    `interval`, zaman kayması birikimine tabidir. Belirli bir mutlak zamanda hassas olaylara ihtiyacınız varsa, her sürenin bitiminde bir sonraki zamana olan fark ile yeni bir zamanlayıcı oluşturun.


!!! not
    Bir `Timer`, durumunu güncellemek için yield noktalarına ihtiyaç duyar. Örneğin, `isopen(t::Timer)` bir yield etmeyen while döngüsünde zaman aşımına uğratılamaz.

