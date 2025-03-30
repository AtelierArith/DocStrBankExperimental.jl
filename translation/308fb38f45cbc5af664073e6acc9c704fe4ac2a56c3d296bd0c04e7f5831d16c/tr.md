```
unsafe_string(p::Ptr{UInt8}, [length::Integer])
```

C tarzı (NUL ile sonlandırılmış) UTF-8 olarak kodlanmış bir stringi bir adresten kopyalar. (Pointer daha sonra güvenle serbest bırakılabilir.) Eğer `length` belirtilmişse (verinin byte cinsinden uzunluğu), string NUL ile sonlandırılmak zorunda değildir.

Bu fonksiyon "güvensiz" olarak etiketlenmiştir çünkü `p`, istenen uzunluktaki veriye geçerli bir bellek adresi değilse çökmesine neden olur.
