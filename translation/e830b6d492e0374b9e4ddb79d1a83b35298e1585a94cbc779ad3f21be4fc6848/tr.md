```
format(dt::TimeType, format::AbstractString; locale="türkçe") -> AbstractString
```

Bir `TimeType` nesnesi kullanarak ve sağlanan `format`'ı uygulayarak bir dize oluşturun. Aşağıdaki karakter kodları `format` dizesini oluşturmak için kullanılabilir:

| Kod | Örnekler | Açıklama                                       |
|:--- |:-------- |:---------------------------------------------- |
| `y` | 6        | Sabit genişlikte sayısal yıl                   |
| `Y` | 1996     | Minimum genişlikte sayısal yıl                 |
| `m` | 1, 12    | Minimum genişlikte sayısal ay                  |
| `u` | Jan      | `locale`'a göre 3 karaktere kısaltılmış ay adı |
| `U` | January  | `locale` anahtar kelimesine göre tam ay adı    |
| `d` | 1, 31    | Minimum genişlikte ayın günü                   |
| `H` | 0, 23    | Minimum genişlikte saat (24 saatlik saat)      |
| `M` | 0, 59    | Minimum genişlikte dakika                      |
| `S` | 0, 59    | Minimum genişlikte saniye                      |
| `s` | 000, 500 | Minimum genişlikte 3 haneli milisaniye         |
| `e` | Mon, Tue | Kısaltılmış hafta günleri                      |
| `E` | Monday   | Haftanın tam günü adı                          |

Ardışık kod karakterlerinin sayısı, kodun genişliğini belirtir. `yyyy-mm` formatı, `y` kodunun dört genişliğe sahip olmasını, `m` kodunun ise iki genişliğe sahip olmasını belirtir. Sayısal rakamlar üreten kodların bir mod ile ilişkisi vardır: sabit genişlik veya minimum genişlik. Sabit genişlik modu, belirtilen genişlikten daha kısa olduğunda değeri sıfırlarla soldan doldurur ve daha uzun olduğunda değeri keser. Minimum genişlik modu, genişlikten daha uzun olan değerleri kesmeden sabit genişlik gibi çalışır.

Bir `format` oluştururken, ayırıcı olarak herhangi bir kod dışı karakter kullanabilirsiniz. Örneğin "1996-01-15T00:00:00" dizesini oluşturmak için `format`: "yyyy-mm-ddTHH:MM:SS" kullanabilirsiniz. Bir kod karakterini literal olarak kullanmanız gerektiğinde, kaçış karakteri ters eğik çizgi kullanabilirsiniz. "1996y01m" dizesi "yyyy\ymm\m" formatı ile üretilebilir.
