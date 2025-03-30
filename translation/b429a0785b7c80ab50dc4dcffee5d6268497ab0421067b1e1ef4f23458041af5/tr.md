```
BileşenHatası
```

Bir [`Görev`](@ref) tarafından atılan istisnaların bir `Vector`'ını (örneğin, bir kanaldan uzaktan çalışan bir işçi tarafından üretilen veya asenkron olarak yürütülen yerel G/Ç yazma işlemi veya `pmap` altında bir uzaktan işçi) istisnaların dizisi hakkında bilgi ile sarmalayın. Örneğin, bir grup işçi birkaç görevi yürütüyorsa ve birden fazla işçi başarısız olursa, ortaya çıkan `BileşenHatası`, her işçiden nerede ve neden istisna(lar)ın meydana geldiğini belirten bir "paket" bilgi içerecektir.
