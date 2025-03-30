```
@code_typed
```

Fonksiyon veya makro çağrısının argümanlarını değerlendirir, türlerini belirler ve elde edilen ifadeye [`code_typed`](@ref) çağrısı yapar. Ek optimizasyonların, örneğin inline işlemlerinin de uygulanıp uygulanmayacağını kontrol etmek için isteğe bağlı `optimize` argümanını kullanın:

```
@code_typed optimize=true foo(x)
```

Ayrıca bakınız: [`code_typed`](@ref), [`@code_warntype`](@ref), [`@code_lowered`](@ref), [`@code_llvm`](@ref), [`@code_native`](@ref).
