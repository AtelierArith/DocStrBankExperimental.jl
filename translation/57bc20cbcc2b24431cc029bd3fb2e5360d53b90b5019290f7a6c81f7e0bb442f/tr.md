```
dlsym_e(handle, sym)
```

Paylaşılan bir kütüphane tutamacından bir sembol arayın, arama başarısız olursa sessizce `C_NULL` döndürün. Bu yöntem artık `dlsym(handle, sym; throw_error=false)` lehine kullanımdan kaldırılmıştır.
