```
artifact_path(hash::SHA1; honor_overrides::Bool=true)
```

Bir artefaktı (SHA1 git ağaç hash'i ile tanımlanan) döndürür, kurulum yolunu. Eğer artefakt mevcut değilse, yükleneceği yeri döndürür.

!!! compat "Julia 1.3"
    Bu fonksiyon en az Julia 1.3 gerektirir.

