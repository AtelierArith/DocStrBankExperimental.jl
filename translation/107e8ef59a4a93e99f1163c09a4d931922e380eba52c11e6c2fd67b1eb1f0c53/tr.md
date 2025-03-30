```
pkgversion(m::Module)
```

Modül `m`'yi içe aktaran paketin sürümünü döndürür veya `m` bir paket tarafından içe aktarılmadıysa veya sürüm alanı ayarlanmamış bir paket tarafından içe aktarıldıysa `nothing` döndürür.

Sürüm, paket yüklenirken paketin Project.toml dosyasından okunur.

Mevcut modülü içe aktaran paketin sürümünü almak için `pkgversion(@__MODULE__)` biçimi kullanılabilir.

!!! compat "Julia 1.9"
    Bu fonksiyon Julia 1.9'da tanıtılmıştır.

