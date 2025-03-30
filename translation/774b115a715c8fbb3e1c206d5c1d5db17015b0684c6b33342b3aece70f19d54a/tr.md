```
@code_llvm
```

Fonksiyon veya makro çağrısının argümanlarını değerlendirir, türlerini belirler ve elde edilen ifadeye [`code_llvm`](@ref) çağrısı yapar. İsteğe bağlı anahtar kelime argümanlarını `raw`, `dump_module`, `debuginfo`, `optimize` olarak ayarlamak için bunları ve değerlerini fonksiyon çağrısından önce koyun, şöyle:

```
@code_llvm raw=true dump_module=true debuginfo=:default f(x)
@code_llvm optimize=false f(x)
```

`optimize`, ek optimizasyonların, örneğin inline etme gibi, uygulanıp uygulanmayacağını kontrol eder. `raw`, tüm meta verileri ve dbg.* çağrılarını görünür hale getirir. `debuginfo`, kod yorumlarının ayrıntı seviyesini belirtmek için `:source` (varsayılan) veya `:none` olabilir. `dump_module`, fonksiyonu kapsayan tüm modülü yazdırır.

Ayrıca bakınız: [`code_llvm`](@ref), [`@code_warntype`](@ref), [`@code_typed`](@ref), [`@code_lowered`](@ref), [`@code_native`](@ref).
