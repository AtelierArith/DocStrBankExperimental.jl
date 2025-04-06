```
@test_deprecated [pattern] expression
```

`--depwarn=yes` olduğunda, `expression`'ın bir deprecasyon uyarısı yaydığını test edin ve `expression`'ın değerini döndürün. Log mesajı dizesi, varsayılan olarak `r"deprecated"i` olan `pattern` ile eşleşecektir.

`--depwarn=no` olduğunda, sadece `expression`'ın çalıştırılmasının sonucunu döndürün. `--depwarn=error` olduğunda, bir ErrorException'ın fırlatıldığını kontrol edin.

# Örnekler

```
# Julia 0.7'de kullanımdan kaldırıldı
@test_deprecated num2hex(1)

# Döndürülen değer, @test ile zincirleme yapılarak test edilebilir:
@test (@test_deprecated num2hex(1)) == "0000000000000001"
```
