```
add!(repo::GitRepo, files::AbstractString...; flags::Cuint = Consts.INDEX_ADD_DEFAULT)
add!(idx::GitIndex, files::AbstractString...; flags::Cuint = Consts.INDEX_ADD_DEFAULT)
```

`files` ile belirtilen yollarla tüm dosyaları `idx` (veya `repo`'nun indeksine) ekleyin. Eğer dosya zaten mevcutsa, indeks girişi güncellenecektir. Eğer dosya zaten mevcut değilse, indeksin içine yeni olarak eklenecektir. `files`, genişletilecek ve eşleşen dosyaların ekleneceği glob desenlerini içerebilir (aşağıda belirtilen `INDEX_ADD_DISABLE_PATHSPEC_MATCH` ayarı yapılmadığı sürece). Eğer bir dosya göz ardı edilmişse (`.gitignore` içinde veya yapılandırmada), *eklenmeyecek*, *ancak* zaten indeks içinde izleniyorsa, o zaman *güncellenecektir*. `flags` anahtar kelime argümanı, göz ardı edilen dosyalarla ilgili davranışı kontrol eden bir bit bayrağı setidir:

  * `Consts.INDEX_ADD_DEFAULT` - yukarıda tanımlanan varsayılan.
  * `Consts.INDEX_ADD_FORCE` - mevcut göz ardı kurallarını dikkate almadan dosyanın indeksine eklenmesini zorlar, eğer zaten göz ardı ediliyorsa bile.
  * `Consts.INDEX_ADD_CHECK_PATHSPEC` - `INDEX_ADD_FORCE` ile aynı anda kullanılamaz. Diskte mevcut olan `files` içindeki her dosyanın göz ardı listesinde olmadığını kontrol eder. Eğer dosyalardan biri *göz ardı edilmişse*, fonksiyon `EINVALIDSPEC` döndürecektir.
  * `Consts.INDEX_ADD_DISABLE_PATHSPEC_MATCH` - glob eşleştirmeyi kapatır ve yalnızca `files` içinde belirtilen yollarla tam olarak eşleşen dosyaları indekse ekler.
