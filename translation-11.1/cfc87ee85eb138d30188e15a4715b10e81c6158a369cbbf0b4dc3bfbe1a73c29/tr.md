```
symlink(target::AbstractString, link::AbstractString; dir_target = false)
```

`link` adında bir sembolik bağlantı oluşturur ve bu bağlantı `target`'a işaret eder.

Windows'ta, sembolik bağlantılar açıkça bir dizine veya değil olarak tanımlanmalıdır. Eğer `target` zaten mevcutsa, varsayılan olarak `link`'in türü otomatik olarak algılanır; ancak `target` mevcut değilse, bu işlev varsayılan olarak bir dosya sembolik bağlantısı oluşturur, `dir_target` `true` olarak ayarlanmadıkça. Kullanıcı `dir_target`'ı ayarlarsa ancak `target` mevcutsa ve bir dosya ise, yine de bir dizin sembolik bağlantısı oluşturulacaktır, ancak sembolik bağlantıyı çözümleme işlemi başarısız olacaktır; tıpkı kullanıcının bir dosya sembolik bağlantısı oluşturması (dizin oluşturulmadan önce `dir_target` `false` olarak ayarlanmış `symlink()` çağrısı yaparak) ve bunu bir dizine çözümlemeye çalışması gibi.

Ayrıca, Windows'ta bir bağlantı oluşturmanın iki yöntemi vardır; sembolik bağlantılar ve kesişim noktaları. Kesişim noktaları biraz daha verimlidir, ancak göreli yolları desteklemez, bu nedenle göreli bir dizin sembolik bağlantısı talep edilirse (bu, `isabspath(target)`'ın `false` döndürmesiyle belirtilir) bir sembolik bağlantı kullanılacaktır, aksi takdirde bir kesişim noktası kullanılacaktır. Windows'ta sembolik bağlantılar oluşturmanın en iyi uygulaması, yalnızca referans verdikleri dosyalar/dizinler zaten oluşturulduktan sonra bunları oluşturmaktır.

Ayrıca bakınız: [`hardlink`](@ref).

!!! not
    Bu işlev, Windows XP gibi yumuşak sembolik bağlantıları desteklemeyen işletim sistemlerinde bir hata oluşturur.


!!! uyumluluk "Julia 1.6"
    `dir_target` anahtar argümanı Julia 1.6'da eklendi. Bunun öncesinde, Windows'ta mevcut olmayan yollara yapılan sembolik bağlantılar her zaman dosya sembolik bağlantıları olurdu ve dizinlere göreli sembolik bağlantılar desteklenmiyordu.

