```
TestCounts
```

Test setinin sonuçlarını görüntüleme amaçları için özyinelemeli olarak toplamak için durumu tutar.

Alanlar:

  * `customized`: `get_test_counts` fonksiyonunun bu sayım nesnesi için özelleştirilip özelleştirilmediği `AbstractTestSet`. Eğer özel bir yöntem tanımlandıysa, her zaman yapıcıya `true` geçin.
  * `passes`: Geçen `@test` çağrılarının sayısı.
  * `fails`: Başarısız olan `@test` çağrılarının sayısı.
  * `errors`: Hata veren `@test` çağrılarının sayısı.
  * `broken`: Bozuk olan `@test` çağrılarının sayısı.
  * `passes`: Geçen `@test` çağrılarının kümülatif sayısı.
  * `fails`: Başarısız olan `@test` çağrılarının kümülatif sayısı.
  * `errors`: Hata veren `@test` çağrılarının kümülatif sayısı.
  * `broken`: Bozuk olan `@test` çağrılarının kümülatif sayısı.
  * `duration`: Söz konusu `AbstractTestSet`'in çalıştığı toplam süre, biçimlendirilmiş bir `String` olarak.
