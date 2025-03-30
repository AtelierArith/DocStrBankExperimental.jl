```
DomainError(val)
DomainError(val, msg)
```

Bir fonksiyon veya yapıcıya verilen `val` argümanı geçerli alanın dışındadır.

# Örnekler

```jldoctest
julia> sqrt(-1)
HATA: DomainError ile -1.0:
sqrt negatif bir reel argüman ile çağrıldı ancak yalnızca karmaşık bir argüman ile çağrıldığında karmaşık bir sonuç döndürecektir. sqrt(Complex(x)) ile denemeyi deneyin.
Stacktrace:
[...]
```
