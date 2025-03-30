```
ImmutableDict
```

`ImmutableDict`, birçok bireysel ekleme ile oluşturulan küçük sözlükler için optimal olan, değiştirilemez bir bağlı liste olarak uygulanmış bir sözlüktür. Bir değeri kaldırmak mümkün değildir, ancak aynı anahtarla yeni bir değer ekleyerek kısmen geçersiz kılınabilir ve gizlenebilir.

```
ImmutableDict(KV::Pair)
```

`key => value` çifti için `ImmutableDict` içinde yeni bir giriş oluşturun

  * bu belirli kombinasyonun özellikler kümesinde olup olmadığını görmek için `(key => value) in dict` kullanın
  * belirli bir anahtar için en son değeri almak için `get(dict, key, default)` kullanın
