```
isexecutable(path::String)
```

Verilen `path`'in çalıştırılabilir izinlere sahip olup olmadığını kontrol eder ve `true` döner.

!!! note
    Bu izin, kullanıcının `path`'i çalıştırmadan önce değişebilir, bu nedenle önce dosyayı çalıştırmak ve hata oluşursa bunu ele almak, `isexecutable`'ı çağırmaktan daha iyi bir yaklaşımdır.


!!! note
    Julia 1.6'dan önce, bu Windows'taki dosya sistemi ACL'lerini doğru bir şekilde sorgulamıyordu, bu nedenle herhangi bir dosya için `true` dönerdi. Julia 1.6'dan itibaren, dosyanın çalıştırılabilir olarak işaretlenip işaretlenmediğini doğru bir şekilde belirler.


Ayrıca bkz. [`ispath`](@ref), [`isreadable`](@ref), [`iswritable`](@ref).
