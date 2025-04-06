```
LogRecord
```

Tek bir günlük olayının sonuçlarını saklar. Alanlar:

  * `level`: günlük mesajının [`LogLevel`](@ref) seviyesi
  * `message`: günlük mesajının metinsel içeriği
  * `_module`: günlük olayının modülü
  * `group`: günlük grubu (varsayılan olarak, günlük olayını içeren dosyanın adı)
  * `id`: günlük olayının kimliği
  * `file`: günlük olayını içeren dosya
  * `line`: günlük olayının dosya içindeki satırı
  * `kwargs`: günlük olayına geçirilen herhangi bir anahtar kelime argümanı
