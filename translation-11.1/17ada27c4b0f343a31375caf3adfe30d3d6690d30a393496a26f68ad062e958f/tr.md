```
@test_nowarn expr
```

`expr` ifadesinin değerlendirilmesinin boş [`stderr`](@ref) çıktısı (uyarılar veya diğer mesajlar olmadan) ile sonuçlanıp sonuçlanmadığını test eder. `expr` ifadesinin değerlendirilmesinin sonucunu döndürür.

Not: `@warn` tarafından üretilen uyarıların yokluğunun bu makro ile test edilemeyeceğini unutmayın. Bunun yerine [`@test_logs`](@ref) kullanın.
