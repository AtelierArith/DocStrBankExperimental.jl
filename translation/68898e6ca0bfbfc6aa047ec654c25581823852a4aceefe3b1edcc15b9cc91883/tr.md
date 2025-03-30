```
message(c::GitCommit, raw::Bool=false)
```

`c` commitinde yapılan değişiklikleri tanımlayan commit mesajını döndürür. Eğer `raw` `false` ise, biraz "temizlenmiş" bir mesaj döndürülür (bu, herhangi bir baştaki yeni satırın kaldırıldığı anlamına gelir). Eğer `raw` `true` ise, mesaj bu tür yeni satırlardan arındırılmaz.
