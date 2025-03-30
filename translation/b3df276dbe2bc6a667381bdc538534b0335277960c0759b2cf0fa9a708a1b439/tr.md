```
Base.isprecompiled(pkg::PkgId; ignore_loaded::Bool=false)
```

Verilen bir PkgId'nin aktif projede önceden derlenip derlenmediğini döndürür.

Varsayılan olarak bu kontrol, farklı sürümlerin yüklü olduğu durumlarda kod yüklemenin gözlemlediği aynı yaklaşımı izler. Yüklenmiş modülleri göz ardı etmek ve sanki yeni bir julia oturumundaymış gibi cevap vermek için `ignore_loaded=true` belirtin.

!!! compat "Julia 1.10"
    Bu fonksiyon en az Julia 1.10 gerektirir.

