```
fetch(t::Task)
```

Bir [`Task`](@ref) tamamlanmasını bekleyin, ardından sonuç değerini döndürün. Görev bir istisna ile başarısız olursa, başarısız görevi saran bir [`TaskFailedException`](@ref) fırlatılır.
