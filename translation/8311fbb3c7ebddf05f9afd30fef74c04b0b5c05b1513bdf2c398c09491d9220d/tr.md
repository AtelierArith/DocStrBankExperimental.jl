```
@r_str -> Regex
```

Bir regex oluşturun, örneğin `r"^[a-z]*$"` gibi, interpolasyon ve kaçış olmadan (tırnak işareti `"` hariç, bu hala kaçırılmalıdır). Regex ayrıca, davranışını değiştirmek için son alıntıdan sonra listelenen bir veya daha fazla bayrağı kabul eder:

  * `i` büyük/küçük harf duyarsız eşleşmeyi etkinleştirir
  * `m` `^` ve `$` belirteçlerini tüm dize yerine bireysel satırların başlangıç ve sonunu eşleyecek şekilde işler.
  * `s` `.` belirtecinin yeni satırları eşlemesine izin verir.
  * `x` "serbest boşluk modu"nu etkinleştirir: regex belirteçleri arasındaki boşluklar, `\` ile kaçırılmadıkça yok sayılır ve regex içindeki `#` bir yorumun başlangıcı olarak kabul edilir (bu, satır sonuna kadar yok sayılır).
  * `a` ASCII modunu etkinleştirir (UTF ve UCP modlarını devre dışı bırakır). Varsayılan olarak `\B`, `\b`, `\D`, `\d`, `\S`, `\s`, `\W`, `\w` vb. Unicode karakter özelliklerine dayalı olarak eşleşir. Bu seçenekle, bu diziler yalnızca ASCII karakterlerini eşleştirir. Bu, belirtilen karakter değerini doğrudan tek bir bayt olarak çıkaracak olan `\u` için de geçerlidir ve UTF-8'e kodlamaya çalışmaz. Önemli olarak, bu seçenek, hem eşleştirici hem de hedefin basit baytlar olarak ele alınmasını sağlayarak geçersiz UTF-8 dizeleriyle eşleşmeye izin verir (sanki ISO/IEC 8859-1 / Latin-1 baytlarıymış gibi) ve genellikle `s` ile birleştirilir. Bu seçenek, deseni `(*UCP)` veya `(*UTF)` ile başlatarak daha da rafine edilebilir.

Interpolasyon gerekiyorsa [`Regex`](@ref) kısmına bakın.

# Örnekler

```jldoctest
julia> match(r"a+.*b+.*?d$"ism, "Goodbye,\nOh, angry,\nBad world\n")
RegexMatch("angry,\nBad world")
```

Bu regex'in ilk üç bayrağı etkinleştirilmiştir.
