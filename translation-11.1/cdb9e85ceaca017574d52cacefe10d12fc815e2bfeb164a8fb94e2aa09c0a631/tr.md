```
DateFormat(format::AbstractString, locale="türkçe") -> DateFormat
```

Tarih dize'lerini ayrıştırmak veya bir tarih nesnesini dize olarak biçimlendirmek için kullanılabilecek bir tarih biçimlendirme nesnesi oluşturur. Aşağıdaki karakter kodları `format` dizesini oluşturmak için kullanılabilir:

| Kod        | Eşleşir   | Açıklama                                                                     |
|:---------- |:--------- |:---------------------------------------------------------------------------- |
| `Y`        | 1996, 96  | 1996, 0096 yılını döndürür                                                   |
| `y`        | 1996, 96  | `parse` üzerinde `Y` ile aynı ancak `format` üzerinde fazla basamakları atar |
| `m`        | 1, 01     | 1 veya 2 basamaklı ayları eşleştirir                                         |
| `u`        | Oca       | `locale` anahtar kelimesine göre kısaltılmış ayları eşleştirir               |
| `U`        | Ocak      | `locale` anahtar kelimesine göre tam ay adlarını eşleştirir                  |
| `d`        | 1, 01     | 1 veya 2 basamaklı günleri eşleştirir                                        |
| `H`        | 00        | Saatleri (24 saatlik saat) eşleştirir                                        |
| `I`        | 00        | 12 saatlik saat ile saatleri çıkarmak için                                   |
| `M`        | 00        | Dakikaları eşleştirir                                                        |
| `S`        | 00        | Saniyeleri eşleştirir                                                        |
| `s`        | .500      | Milisaniyeleri eşleştirir                                                    |
| `e`        | Paz, Sal  | Kısaltılmış haftanın günlerini eşleştirir                                    |
| `E`        | Pazartesi | Haftanın günlerinin tam adını eşleştirir                                     |
| `p`        | AM        | AM/PM'yi (büyük/küçük harf duyarsız) eşleştirir                              |
| `yyyymmdd` | 19960101  | Sabit genişlikte yıl, ay ve günü eşleştirir                                  |

Yukarıda listelenmeyen karakterler genellikle tarih ve saat dilimleri arasındaki ayırıcılar olarak kabul edilir. Örneğin, "1996-01-15T00:00:00.0" dizesinin `format` dizesi "y-m-dTH:M:S.s" gibi olacaktır. Bir kod karakterini ayırıcı olarak kullanmanız gerekiyorsa, onu ters eğik çizgi ile kaçırabilirsiniz. "1995y01m" tarihi "y\ym\m" formatına sahip olacaktır.

12:00AM'nin 00:00 (gece yarısı) ile, 12:00PM'nin 12:00 (öğle) ile eşleştiğini unutmayın. `p` belirteci ile bir zamanı ayrıştırırken, herhangi bir saat (ister `H` ister `I`) 12 saatlik saat olarak yorumlanır, bu nedenle `I` kodu esasen çıktı için faydalıdır.

Bir DateFormat nesnesi oluşturmak maliyetlidir. Mümkün olduğunda, bir kez oluşturun ve birçok kez kullanın veya [`dateformat""`](@ref @dateformat_str) dize makrosunu deneyin. Bu makro, DateFormat nesnesini makro genişletme zamanında bir kez oluşturur ve daha sonra yeniden kullanır. Ayrıca, daha sonra listelenen birkaç [önceden tanımlı biçimlendirici](@ref Common-Date-Formatters) vardır.

[`DateTime`](@ref) ve [`format`](@ref) ile bir DateFormat nesnesini tarih dizelerini ayrıştırmak ve yazmak için nasıl kullanacağınızı görün.
