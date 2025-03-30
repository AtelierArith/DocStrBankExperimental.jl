```
catch_exceptions(logger)
```

Logger'ın log kaydı oluşturma sırasında meydana gelen istisnaları yakalayıp yakalamayacağını belirtmek için `true` döner. Varsayılan olarak, mesajlar yakalanır.

Varsayılan olarak, programın çökmesine neden olmamak için tüm istisnalar yakalanır. Bu, kullanıcıların üretim sisteminde nadiren kullanılan işlevselliği - örneğin hata ayıklama kaydı - güvenle açıp kapatmalarını sağlar.

Eğer günlüğü bir denetim izi olarak kullanmak istiyorsanız, bu durumu logger türünüz için devre dışı bırakmalısınız.
