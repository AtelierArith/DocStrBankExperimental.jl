```
code_lowered(f, types; generated=true, debuginfo=:default)
```

Verilen genel işlev ve tür imzasına uyan yöntemlerin düşürülmüş formlarının (IR) bir dizisini döndürür.

Eğer `generated` `false` ise, döndürülen `CodeInfo` örnekleri yedek uygulamalara karşılık gelecektir. Yedek uygulama yoksa bir hata fırlatılır. Eğer `generated` `true` ise, bu `CodeInfo` örnekleri jeneratörleri genişleterek elde edilen yöntem gövdelerine karşılık gelecektir.

Anahtar kelime `debuginfo`, çıktıda bulunan kod meta verisinin miktarını kontrol eder.

Eğer `types` yaprak türler değilse ve ilgili yöntemlerden herhangi biri bir `@generated` yöntemi ise, `generated` `true` olduğunda bir hata fırlatılacağını unutmayın.
