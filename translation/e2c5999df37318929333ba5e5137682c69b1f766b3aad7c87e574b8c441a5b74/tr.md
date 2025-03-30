```
isreadable(path::String)
```

Verilen `path` için erişim izinleri mevcut kullanıcı tarafından okuma izni veriyorsa `true` döner.

!!! note
    Bu izin, kullanıcının `open` çağrısından önce değişebilir, bu nedenle önce `isreadable` çağırmak yerine yalnızca `open` çağırıp hata durumunu ele almak önerilir.


!!! note
    Şu anda bu fonksiyon Windows'taki dosya sistemi ACL'lerini doğru bir şekilde sorgulamıyor, bu nedenle yanlış sonuçlar döndürebilir.


!!! compat "Julia 1.11"
    Bu fonksiyon en az Julia 1.11 gerektirir.


Ayrıca bkz. [`ispath`](@ref), [`isexecutable`](@ref), [`iswritable`](@ref).
