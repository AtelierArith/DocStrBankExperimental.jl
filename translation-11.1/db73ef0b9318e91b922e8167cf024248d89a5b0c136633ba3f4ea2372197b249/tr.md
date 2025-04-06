```
eigen(A::Union{SymTridiagonal, Hermitian, Symmetric}, irange::UnitRange) -> Eigen
```

`A`'n özdeğer ayrıştırmasını hesaplayarak, özdeğerleri `F.values` içinde ve özvektörleri matris `F.vectors`'ın sütunlarında içeren bir [`Eigen`](@ref) faktörizasyon nesnesi `F` döndürür. (`k`'nci özvektör, `F.vectors[:, k]` diliminden elde edilebilir.)

Ayrıştırmayı yineleyerek `F.values` ve `F.vectors` bileşenlerini elde edebilirsiniz.

`Eigen` nesneleri için aşağıdaki fonksiyonlar mevcuttur: [`inv`](@ref), [`det`](@ref) ve [`isposdef`](@ref).

[`UnitRange`](@ref) `irange`, aranan sıralı özdeğerlerin indekslerini belirtir.

!!! not
    Eğer `irange` `1:n` değilse, burada `n` `A`'nın boyutudur, o zaman döndürülen faktörizasyon *kısmi* bir faktörizasyon olacaktır.

