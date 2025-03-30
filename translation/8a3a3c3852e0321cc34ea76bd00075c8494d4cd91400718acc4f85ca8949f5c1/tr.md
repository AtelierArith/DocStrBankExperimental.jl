```
@code_native
```

Fonksiyon veya makro çağrısının argümanlarını değerlendirir, türlerini belirler ve sonuçlanan ifadeye [`code_native`](@ref) çağrısı yapar.

İsteğe bağlı anahtar argümanlardan herhangi birini `syntax`, `debuginfo`, `binary` veya `dump_module` olarak ayarlamak için, bunu fonksiyon çağrısından önce koyun, şöyle:

```
@code_native syntax=:intel debuginfo=:default binary=true dump_module=false f(x)
```

  * Montaj sözdizimini ayarlamak için `syntax`'ı Intel sözdizimi için `:intel` (varsayılan) veya AT&T sözdizimi için `:att` olarak ayarlayın.
  * Kod yorumlarının ayrıntılılığını ayarlamak için `debuginfo`'yu `:source` (varsayılan) veya `:none` olarak ayarlayın.
  * `binary` `true` ise, her talimat için kısaltılmış bir adresle birlikte ikili makine kodunu da yazdırın.
  * `dump_module` `false` ise, rodata veya direktifler gibi meta verileri yazdırmayın.

Ayrıca bakınız: [`code_native`](@ref), [`@code_warntype`](@ref), [`@code_typed`](@ref), [`@code_lowered`](@ref), [`@code_llvm`](@ref).
