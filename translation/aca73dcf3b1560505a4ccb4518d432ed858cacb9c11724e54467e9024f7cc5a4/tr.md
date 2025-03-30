```
unsafe_pointer_to_objref(p::Ptr)
```

Bir `Ptr`'yi bir nesne referansına dönüştürür. İşaretçinin geçerli bir yığın üzerinde tahsis edilmiş Julia nesnesine atıfta bulunduğu varsayılmaktadır. Eğer durum böyle değilse, tanımsız bir davranış ortaya çıkar, bu nedenle bu fonksiyon "güvensiz" olarak kabul edilir ve dikkatle kullanılmalıdır.

Ayrıca bkz. [`pointer_from_objref`](@ref).
