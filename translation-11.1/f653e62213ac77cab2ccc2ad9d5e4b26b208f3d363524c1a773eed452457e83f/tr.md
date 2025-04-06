```
Char(c::Union{Number,AbstractChar})
```

`Char`, Julia'daki karakterlerin varsayılan temsilidir ve 32 bitlik bir [`AbstractChar`](@ref) türüdür. `Char`, `'x'` gibi karakter literalleri için kullanılan türdür ve aynı zamanda [`String`](@ref) türünün eleman türüdür.

Bir `String` içinde saklanan rastgele bayt akışlarını kayıpsız bir şekilde temsil etmek için, bir `Char` değeri Unicode kod noktasına dönüştürülemeyen bilgileri depolayabilir — böyle bir `Char`'ı `UInt32`'ye dönüştürmek bir hata fırlatır. `c`'nin geçerli bir Unicode karakterini temsil edip etmediğini sorgulamak için [`isvalid(c::Char)`](@ref) fonksiyonu kullanılabilir.
