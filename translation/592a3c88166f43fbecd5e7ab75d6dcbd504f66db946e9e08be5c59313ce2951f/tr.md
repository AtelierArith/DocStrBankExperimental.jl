```
@big_str str
```

Bir dizeyi [`BigInt`](@ref) veya [`BigFloat`](@ref) olarak ayrıştırın ve dize geçerli bir sayı değilse bir `ArgumentError` fırlatın. Tam sayılar için `_` dizede bir ayırıcı olarak kullanılabilir.

# Örnekler

```jldoctest
julia> big"123_456"
123456

julia> big"7891.5"
7891.5

julia> big"_"
HATA: ArgumentError: BigInt veya BigFloat için geçersiz sayı formatı _
[...]
```

!!! uyarı     [`BigFloat`](@ref) değerleri oluşturmak için `@big_str` kullanmak, naif olarak beklenebilecek davranışı sağlamayabilir: bir makro olarak `@big_str`, *yükleme zamanı* itibarıyla mevcut olan global hassasiyet ([`setprecision`](@ref)) ve yuvarlama modu ([`setrounding`](@ref)) ayarlarına uyar. Bu nedenle, `() -> precision(big"0.3")` gibi bir fonksiyon, fonksiyonun tanımlandığı andaki hassasiyet değerine bağlı olan sabit bir değer döndürür, **fonksiyonun çağrıldığı zamandaki** hassasiyete değil.
