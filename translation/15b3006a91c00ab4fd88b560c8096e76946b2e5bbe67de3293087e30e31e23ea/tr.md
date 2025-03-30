```
eigen(A::Union{SymTridiagonal, Hermitian, Symmetric}, vl::Real, vu::Real) -> Eigen
```

`A`'n özdeğer ayrıştırmasını hesaplayarak, özdeğerleri `F.values` içinde ve özvektörleri matris `F.vectors`'ın sütunlarında içeren bir [`Eigen`](@ref) faktörizasyon nesnesi `F` döndürür. (`k`'nci özvektör, `F.vectors[:, k]` diliminden elde edilebilir.)

Ayrıştırmayı yineleyerek `F.values` ve `F.vectors` bileşenlerini elde edebilirsiniz.

`Eigen` nesneleri için aşağıdaki fonksiyonlar mevcuttur: [`inv`](@ref), [`det`](@ref) ve [`isposdef`](@ref).

`vl`, aramak için özdeğerlerin alt sınırıdır ve `vu` üst sınırdır.

!!! not
    Eğer [`vl`, `vu`] `A`'nın tüm özdeğerlerini içermiyorsa, döndürülen faktörizasyon *kısmi* bir faktörizasyon olacaktır.

