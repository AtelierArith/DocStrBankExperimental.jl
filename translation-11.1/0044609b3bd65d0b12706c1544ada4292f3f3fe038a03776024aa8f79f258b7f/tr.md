```
tempname(parent=tempdir(); cleanup=true) -> String
```

Geçici bir dosya yolu oluşturur. Bu fonksiyon yalnızca bir yol döndürür; dosya oluşturulmaz. Yolın benzersiz olması muhtemeldir, ancak `tempname`'e iki eşzamanlı çağrının aynı dosya adını oluşturma olasılığı nedeniyle bu garanti edilemez. İsim, `tempname` çağrısı sırasında zaten mevcut olan tüm dosyalardan farklı olacağı garanti edilir.

Hiçbir argüman verilmeden çağrıldığında, geçici ad, `tempdir()` tarafından verilen sistem geçici dizininde bir geçici ad için mutlak bir yol olacaktır. Eğer bir `parent` dizin argümanı verilirse, geçici yol bunun yerine o dizinde olacaktır.

`cleanup` seçeneği, işlemin çıkış yaptığında döndürülen yolu otomatik olarak silmeye çalışıp çalışmayacağını kontrol eder. `tempname` fonksiyonu döndürülen konumda herhangi bir dosya veya dizin oluşturmadığı için, orada bir dosya veya dizin oluşturmadığınız sürece silinecek bir şey yoktur. Eğer bir dosya veya dizin oluşturursanız ve `cleanup` `true` ise, işlem sona erdiğinde silinecektir.

!!! compat "Julia 1.4"
    `parent` ve `cleanup` argümanları 1.4'te eklendi. Julia 1.4'ten önce `tempname`'in yolu işlem sona erdiğinde asla temizlenmeyecekti.


!!! warning
    Bu, başka bir işlemin aynı dosya adını alması ve dosyayı sizden önce oluşturması durumunda güvenlik açıklarına yol açabilir. Bu bir endişe ise dosyayı `JL_O_EXCL` ile açın. Bunun yerine [`mktemp()`](@ref) kullanılması da önerilir.

