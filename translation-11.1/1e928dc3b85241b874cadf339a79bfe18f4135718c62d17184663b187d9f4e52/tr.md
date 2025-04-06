```
code_typed(f, types; kw...)
```

Verilen genel işlev ve tür imzasına uyan yöntemler için tür çıkarımlı alt form (IR) dizisi döndürür.

# Anahtar Argümanlar

  * `optimize::Bool = true`: isteğe bağlı, ek optimizasyonların, örneğin iç içe alma gibi, uygulanıp uygulanmayacağını kontrol eder.
  * `debuginfo::Symbol = :default`: isteğe bağlı, çıktıda bulunan kod meta verisinin miktarını kontrol eder, olası seçenekler `:source` veya `:none`'dır.

# Dahili Anahtar Argümanlar

Bu bölüm dahili olarak kabul edilmeli ve yalnızca Julia derleyici iç işleyişini anlayanlar için geçerlidir.

  * `world::UInt = Base.get_world_counter()`: isteğe bağlı, yöntemleri ararken kullanılacak dünya yaşını kontrol eder, belirtilmezse mevcut dünya yaşı kullanılır.
  * `interp::Core.Compiler.AbstractInterpreter = Core.Compiler.NativeInterpreter(world)`: isteğe bağlı, kullanılacak soyut yorumlayıcıyı kontrol eder, belirtilmezse yerel yorumlayıcı kullanılır.

# Örnekler

Argüman türlerini bir demet içinde koyarak karşılık gelen `code_typed`'i alabilirsiniz.

```julia
julia> code_typed(+, (Float64, Float64))
1-element Vector{Any}:
 CodeInfo(
1 ─ %1 = Base.add_float(x, y)::Float64
└──      return %1
) => Float64
```
