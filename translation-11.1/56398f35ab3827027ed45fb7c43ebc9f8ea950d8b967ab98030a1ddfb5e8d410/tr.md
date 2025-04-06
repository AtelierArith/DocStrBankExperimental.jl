```
@test_warn msg expr
```

`expr` ifadesinin değerlendirilmesinin `msg` dizesini içeren veya `msg` düzenli ifadesiyle eşleşen [`stderr`](@ref) çıktısına neden olup olmadığını test eder. Eğer `msg` bir boolean fonksiyonuysa, `msg(output)` ifadesinin `true` döndürüp döndürmediğini test eder. Eğer `msg` bir demet veya dizi ise, hata çıktısının `msg` içindeki her bir öğeyi içerip içermediğini/kapsayıp kapsamadığını kontrol eder. `expr` ifadesinin değerlendirilmesinin sonucunu döndürür.

Hata çıktısının yokluğunu kontrol etmek için [`@test_nowarn`](@ref) makrosunu da inceleyin.

Not: `@warn` ile üretilen uyarılar bu makro ile test edilemez. Bunun yerine [`@test_logs`](@ref) kullanın.
