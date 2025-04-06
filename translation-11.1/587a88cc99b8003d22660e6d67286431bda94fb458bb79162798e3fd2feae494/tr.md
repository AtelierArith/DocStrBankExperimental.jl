```
code_native([io=stdout,], f, types; syntax=:intel, debuginfo=:default, binary=false, dump_module=true)
```

Verilen genel işlev ve tür imzasına uyan yöntemin çalıştırılması için üretilen yerel montaj talimatlarını `io`ya yazdırır.

  * Montaj sözdizimini ayarlamak için `syntax`'ı `:intel` (varsayılan) olarak intel sözdizimi veya `:att` olarak AT&T sözdizimi için ayarlayın.
  * Kod yorumlarının ayrıntı seviyesini belirtmek için `debuginfo`'yu `:source` (varsayılan) veya `:none` olarak ayarlayın.
  * Eğer `binary` `true` ise, her talimat için kısaltılmış bir adresle birlikte ikili makine kodunu da yazdırın.
  * Eğer `dump_module` `false` ise, rodata veya direktifler gibi meta verileri yazdırmayın.
  * Eğer `raw` `false` ise, ilginç olmayan talimatlar (safepoint işlev prologu gibi) atlanır.

Ayrıca bakınız: [`@code_native`](@ref), [`code_warntype`](@ref), [`code_typed`](@ref), [`code_lowered`](@ref), [`code_llvm`](@ref).
