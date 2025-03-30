```
iswritable(path::String)
```

Verilen `path` için erişim izinleri mevcut kullanıcı tarafından yazmaya izin veriyorsa `true` döner.

!!! note
    Bu izin, kullanıcının `open` çağrısından önce değişebilir, bu nedenle önce `iswritable` çağırmak yerine yalnızca `open` çağırmak ve hata durumunda bunu ele almak önerilir.


!!! note
    Şu anda bu fonksiyon Windows'taki dosya sistemi ACL'lerini doğru bir şekilde sorgulamıyor, bu nedenle yanlış sonuçlar döndürebilir.


!!! compat "Julia 1.11"
    Bu fonksiyon en az Julia 1.11 gerektirir.


Ayrıca bkz. [`ispath`](@ref), [`isexecutable`](@ref), [`isreadable`](@ref).
