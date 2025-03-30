```
names(x::Module; all::Bool = false, imported::Bool = false)
```

Bir `Module`'ün kamuya açık isimlerinin bir vektörünü alın, eski isimleri hariç tutarak. Eğer `all` doğruysa, o zaman liste ayrıca modülde tanımlanan kamuya açık olmayan isimleri, eski isimleri ve derleyici tarafından oluşturulan isimleri de içerir. Eğer `imported` doğruysa, o zaman diğer modüllerden açıkça içe aktarılan isimler de dahil edilir. İsimler sıralı olarak döndürülür.

Özel bir durum olarak, `Main` içinde tanımlanan tüm isimler "kamuya açık" olarak kabul edilir, çünkü `Main`'den gelen isimleri açıkça kamuya açık olarak işaretlemek alışılmış bir durum değildir.

!!! not
    `sym ∈ names(SomeModule)` ifadesi `isdefined(SomeModule, sym)` anlamına gelmez. `names`, modülde tanımlı olmasalar bile `public` veya `export` ile işaretlenmiş sembolleri döndürecektir.


Ayrıca bakınız: [`Base.isexported`](@ref), [`Base.ispublic`](@ref), [`Base.@locals`](@ref), [`@__MODULE__`](@ref).
