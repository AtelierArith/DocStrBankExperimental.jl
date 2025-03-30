```
GenelleştirilmişSchur <: Faktörizasyon
```

İki matris `A` ve `B` için genelleştirilmiş Schur faktörizasyonunun matris faktörizasyon türü. Bu, [`schur(_, _)`](@ref) ile ilgili matris faktörizasyon fonksiyonunun dönüş türüdür.

Eğer `F::GenelleştirilmişSchur` faktörizasyon nesnesi ise, (quasi) üçgen Schur faktörleri `F.S` ve `F.T` aracılığıyla elde edilebilir, sol birim/ortogonal Schur vektörleri `F.left` veya `F.Q` ile, sağ birim/ortogonal Schur vektörleri ise `F.right` veya `F.Z` ile elde edilebilir; böylece `A=F.left*F.S*F.right'` ve `B=F.left*F.T*F.right'`. `A` ve `B`'nin genelleştirilmiş özdeğerleri `F.α./F.β` ile elde edilebilir.

Ayrıştırmayı yinelemek, bileşenleri `F.S`, `F.T`, `F.Q`, `F.Z`, `F.α` ve `F.β` üretir.
