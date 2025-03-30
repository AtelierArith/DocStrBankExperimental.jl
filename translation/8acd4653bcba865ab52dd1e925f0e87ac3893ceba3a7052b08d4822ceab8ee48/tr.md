```
annotate!(str::AnnotatedString, [range::UnitRange{Int}], label::Symbol, value)
annotate!(str::SubString{AnnotatedString}, [range::UnitRange{Int}], label::Symbol, value)
```

Bir `str` (veya tüm dize) için etiketli bir değer (`label` => `value`) ile bir `range`'i anotlayın. Mevcut `label` anotasyonlarını kaldırmak için `nothing` değerini kullanın.

`str` üzerinde anotasyonların uygulanma sırası anlamsal olarak önemlidir; bu, [`AnnotatedString`](@ref) içinde açıklanmıştır.
