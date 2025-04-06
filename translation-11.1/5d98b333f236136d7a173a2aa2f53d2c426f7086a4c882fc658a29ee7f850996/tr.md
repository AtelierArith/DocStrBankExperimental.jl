```
Experimental.show_error_hints(io, ex, args...)
```

Belirli bir istisna türü `typeof(ex)` için [`Experimental.register_error_hint`](@ref) tarafından tüm işleyicileri çağırın. `args`, o tür için işleyici tarafından beklenen diğer argümanları içermelidir.

!!! uyumluluk "Julia 1.5"
    Özel hata ipuçları Julia 1.5 itibarıyla mevcuttur.


!!! uyarı     Bu arayüz deneysel olup, bildirimde bulunmaksızın değişikliğe veya kaldırılmaya tabidir.
