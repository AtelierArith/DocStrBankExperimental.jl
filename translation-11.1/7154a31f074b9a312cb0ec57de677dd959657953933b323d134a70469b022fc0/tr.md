```
poll_file(path::AbstractString, interval_s::Real=5.007, timeout_s::Real=-1) -> (previous::StatStruct, current)
```

Bir dosyayı, bir değişiklik meydana gelene kadar veya `timeout_s` saniye geçene kadar her `interval_s` saniyede bir kontrol ederek izleyin. `interval_s` uzun bir süre olmalıdır; varsayılan değer 5.007 saniyedir.

Bir değişiklik tespit edildiğinde, durum nesnelerinin bir çiftini `(previous, current)` döndürür. `previous` durumu her zaman bir `StatStruct`'tur, ancak tüm alanları sıfırlanmış olabilir (bu, dosyanın daha önce mevcut olmadığını veya daha önce erişilebilir olmadığını gösterir).

`current` durum nesnesi bir `StatStruct`, bir `EOFError` (zaman aşımının dolduğunu gösterir) veya `stat` işleminin başarısız olması durumunda başka bir `Exception` alt türü olabilir (örneğin, yol mevcut değilse).

Bir dosyanın ne zaman değiştirildiğini belirlemek için `current isa StatStruct && mtime(prev) != mtime(current)` karşılaştırmasını kullanarak değişiklik bildirimini tespit edin. Ancak, bu işlem için [`watch_file`](@ref) kullanılması tercih edilir, çünkü daha güvenilir ve etkilidir, ancak bazı durumlarda mevcut olmayabilir.
