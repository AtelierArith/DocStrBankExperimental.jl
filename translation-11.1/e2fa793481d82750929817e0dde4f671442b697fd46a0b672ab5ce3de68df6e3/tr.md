```
isascii(cu::AbstractVector{CU}) where {CU <: Integer} -> Bool
```

Vektördeki tüm değerlerin ASCII karakter kümesine (0x00 ile 0x7f arasında) ait olup olmadığını test eder. Bu fonksiyon, hızlı bir ASCII kontrolüne ihtiyaç duyan diğer string uygulamaları tarafından kullanılmak üzere tasarlanmıştır.
