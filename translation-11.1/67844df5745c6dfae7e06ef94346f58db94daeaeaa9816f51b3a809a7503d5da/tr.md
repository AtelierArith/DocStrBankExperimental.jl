```
code_llvm([io=stdout,], f, types; raw=false, dump_module=false, optimize=true, debuginfo=:default)
```

Verilen genel işlev ve tür imzası için eşleşen yöntemin çalıştırılması için üretilen LLVM bit kodlarını `io`'ya yazdırır.

`optimize` anahtar kelimesi ayarlanmamışsa, kod LLVM optimizasyonlarından önce gösterilecektir. Tüm meta veriler ve dbg.* çağrıları basılan bit kodundan kaldırılır. Tam IR için `raw` anahtar kelimesini true olarak ayarlayın. Fonksiyonu kapsayan tüm modülü (deklarasyonlarla birlikte) dökmek için `dump_module` anahtar kelimesini true olarak ayarlayın. Anahtar kelime argümanı `debuginfo`, kod yorumlarının ayrıntı seviyesini belirtmek için kaynak (varsayılan) veya yok olarak biri olabilir.

Ayrıca bakınız: [`@code_llvm`](@ref), [`code_warntype`](@ref), [`code_typed`](@ref), [`code_lowered`](@ref), [`code_native`](@ref).
