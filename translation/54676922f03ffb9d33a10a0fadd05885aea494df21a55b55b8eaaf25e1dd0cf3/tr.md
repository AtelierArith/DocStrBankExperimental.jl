```
ConsoleLogger([stream,] min_level=Info; meta_formatter=default_metafmt,
              show_limited=true, right_justify=0)
```

Metin konsolda okunabilirlik için optimize edilmiş bir Logger, örneğin Julia REPL ile etkileşimli çalışma için.

`min_level`'den daha düşük log seviyeleri filtrelenir.

Mesaj formatı, anahtar argümanlar ayarlanarak kontrol edilebilir:

  * `meta_formatter`, log olayı meta verilerini `(level, _module, group, id, file, line)` alanlarını alıp log mesajı için bir renk (printstyled'e geçilecek şekilde) ve ön ek ve son ek döndüren bir işlevdir. Varsayılan, log seviyesinin ön eki ve modül, dosya ve satır konumunu içeren bir son ek ile ön eklemektir.
  * `show_limited`, büyük veri yapılarını ekrana sığacak bir şeyle sınırlayarak yazdırmayı sınırlar; bu, formatlama sırasında `:limit` `IOContext` anahtarını ayarlayarak yapılır.
  * `right_justify`, log meta verilerinin sağa yaslandığı tam sayı sütunudur. Varsayılan sıfırdır (meta veriler kendi satırında yer alır).
