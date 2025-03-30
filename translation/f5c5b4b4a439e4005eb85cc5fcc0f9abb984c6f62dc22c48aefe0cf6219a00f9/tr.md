```
WeakKeyDict([itr])
```

`WeakKeyDict()` bir hash tablosu oluşturur; burada anahtarlar, bir hash tablosunda referans verilse bile çöp toplayıcı tarafından toplanabilecek nesnelere zayıf referanslardır.

Daha fazla yardım için [`Dict`](@ref) bölümüne bakın. Not: [`Dict`](@ref)'ın aksine, `WeakKeyDict` anahtarları ekleme sırasında dönüştürmez, çünkü bu, anahtar nesnesinin eklemeden önce hiçbir yerde referans verilmediği anlamına gelir.

Ayrıca bkz. [`WeakRef`](@ref).
